---
layout: post
title: 지킬 세팅하기
categories: [jekyll]
tags: [server,jekyll]
fullview: true
comments: true
---

#github 만들기

## github 가입후, repository명 만들기

* github 가입을 한 후에, respository를 다음과 같은 형식으로 만들어야한다

~~~
{계정명}.github.io
~~~

그럼 클론을 받으면 위의 리포지터리명과 동일한 이름의 폴더로 만들어지겠지

~~~
git clone https://github.com/{계정명}/{계정명}.github.io.git
cd {계정명}.github.io.git
~~~

*해당폴더에 올린게 없으니.. 비어있을테고.

#지킬설치
지킬을 sudo gem으로 설치한다

~~~
gem install jekyll

//우리가 아까 만든 git 폴더에 파일들이 생성된다.
jekyll new {계정명}.github.io.git

//현재 파일들을 추가
git add .
git commit -m 'first commit'
git push -u origin master

//서버 실행해보자
jekyll serve --watch

//접속
http://localhost:4000
~~~

* 참고로 _config.yaml 은 수정해도 watch에서 못찾으므로 jekyll serve를 다시 실행해줘야 반영된다

#테마

##테마받기

dbyll이란 테마가 괜찮아 보였다. 특징은

* 카테고리 지원
* 태그지원
* 하얀색의 깔끔한 배경

URL

[dbyll 테마다운](http://dbtek.github.io/dbyll/)


기존에 깔려있던 기본테마를 싹 지우고, 위의 URL에서 압축받은 것을 해당폴더에 넣는다

##설치시 문제
* paginate라는 플러그인을 사용하는 테마라서, 설치를 해줘야한다

~~~
sudo gem install pygments.rb
sudo gem install jekyll-paginate
~~~

* configuration에 아래 줄을 추가해줬다(첫번째줄에)

~~~
gems: [jekyll-paginate]
~~~

그리고 서버 실행해보면 테마가 짠 설정되어있음

~~~
jekyll serve --watch

//http://localhost:4000접속
~~~

## disqus 연동
댓글 달수 있는 disqus 사이트에 회원가입 후, 서비스를 만든다.
https://publishers.disqus.com/

* Unversial Install 눌러서 아래와 같은 코드를 _includes/disqus.html에 넣는다

~~~
    /**
     *  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
     *  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables
     */
    /*
    var disqus_config = function () {
        this.page.url = PAGE_URL;  // Replace PAGE_URL with your page's canonical URL variable
        this.page.identifier = PAGE_IDENTIFIER; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
    };
   ....
   ....


~~~

이메일 인증까지 하면 완료.
