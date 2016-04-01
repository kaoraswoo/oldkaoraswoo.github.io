---
layout: post
title: ssh 비밀번호 없이 접속하기
categories:
- Server
---
> 내 맥에서 리눅스 서버에 ssh로 접속하려는데 맨날 암호 넣기 짜증난다
그러므로 암호없이 접속하게 내 맥을 리모트(리눅스)서버에 정보를 넣어주자

# ssh 비밀번호 없이 접속하기
## 개요
* 내 맥에서 리눅스 서버에 ssh로 접속하려는데 맨날 암호 넣기 짜증난다
* 그러므로 암호없이 접속하게 내 맥을 리모트(리눅스)서버에 정보를 넣어주자

## 아직 내 맥에서 key를 생성안했을시
* 먼저 ssh key를 만들자 
* 그전에 .ssh 폴더에 이미 생성한 id_rsa.pub이 있다면 패스.

```
hwangjehyunui-Mac-mini:~ jhhwang$ cd .ssh
hwangjehyunui-Mac-mini:.ssh jhhwang$ ls
id_rsa		id_rsa.pub	known_hosts
```

### ssh-keygen

```
ssh-keygen -t rsa
```

passphrase 를 입력한다. passphrase는 일종의 비밀번호로 비공개키를 입력한 값으로 암호화한다. 권장 값은 10~30 문자이고 생략 가능하다. 생략하면 이 부분이 보안 홀이 될 수 있기 때문에 주의한다. 자동 로그인을 원한다면 생략해야 한다. 

* 생성된 파일은 다음과 같다
* id_rsa	private key, 절대로 타인에게 노출되면 안된다.
* id_rsa.pub	public key, 접속하려는 리모트 머신의 authorized_keys에 입력한다.
* authorized_keys	리모트 머신의 .ssh 디렉토리 아래에 위치하면서 id_rsa.pub 키의 값을 저장한다. 자세한 내용은 다음 단락을 참조


### 보안설정(옵션)
* .ssh 디렉토리는 매우 중요한 보안 정보가 담긴 디렉토리다. 따라서 퍼미션 설정을 꼭해야 하는데 아래와 같은 설정을 권장한다. 아래의 명령을 순차적으로 실행한다. 퍼미션에 대한 자세한 정보는 생활코딩 리눅스 수업을 참조한다. 

https://opentutorials.org/course/141/1010

```
chmod 700 ~/.ssh
chmod 600 ~/.ssh/id_rsa
chmod 644 ~/.ssh/id_rsa.pub  
chmod 644 ~/.ssh/authorized_keys
chmod 644 ~/.ssh/known_hosts
```

### 내 키파일을 리모트에 복사해넣기

```
scp $HOME/.ssh/id_rsa.pub root@{리모트주소}:id_rsa.pub
ex) scp $HOME/.ssh/id_rsa.pub root@1.234.54.22:id_rsa.pub

id_rsa.pub                                                                                       100%  395     0.4KB/s   00:00 
```


### 리모트에 접속해서 복사한 파일에서 authrozed_keys에 추가하기

* 이제 원격 머신에서 전송한 id_rsa.pub 파일을 authorized_keys 파일에 추가해보자. 
* 아래의 명령에서 cat는 뒤에 따라오는 파일의 내용을 화면에 출력하는 것이고, 
* \>>\ 는 cat이 출력한 내용을 authorized_keys 파일에 추가하는 것이다. 내용을 교체하는 것이 아니라 추가하는 것이라는 점에 주의하자.
* 만약 리모트 머신으로 접속하는 여러개의 로컬 머신이 있다면 각각의 로컬 머신의 id_ras.pub 파일을 authorized_keys에 추가해주면 된다

```
cat $HOME/id_rsa.pub >> $HOME/.ssh/authorized_keys
```


