---
layout: post
title: 블로그에 도메인 사서 연결하기
categories:
- jekyll
---

> 블로그를 구축했으나 다음과 같이 주소가 조금 애매하다. **http://kaoraswoo.github.io**  그러므로 **도메인** 을 구입해서 연결시켜보자!


## CNAME 작성하기

* 내 블로그 root에, CNAME 이라는 파일을 하나 만들어서, 곧 구매할 예정인 아래 url 내용을 넣어주었다 (http 이런거는 쓰지 말자..)

~~~ bash
kaora.co.kr
~~~



#도메인사이트

페이스북에서 국내최저가로 광고하는 이곳을 하나 선정하였다.
[메일플러그](http://www.mailplug.com/)

구입한 주소는

[http://kaora.co.kr](http://kaora.co.kr)

가입후에 천신만고 끝에 구입완료. 자세히 보니 **SelfDNS** 라는 항목이 있구나!

활성화버튼 시켜서 관리 눌러보면, 필요한 부분이

* 별칭(CNAME)

|호스트명|연결주소|
|----|----|
|www.kaora.co.kr|kaora.co.kr|


*  호스트IP(A)

|호스트명|연결주소|
|----|----|
|kaora.co.kr|192.30.252.153|
|www.kaora.co.kr|192.30.252.154|



참고로 **192.30.252.153, 192.30.252.154** 이 IP는 github에서 제공하는 아이피이다.

해당 아이피로 연결한 후에, 아래에서 github메인페이지내에 CNAME을 연동해두면, github에서 찾아서 연동해주는 구조.
