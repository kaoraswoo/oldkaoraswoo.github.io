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

{% highlight bash %}
{계정명}.github.io
{% endhighlight %}

그럼 클론을 받으면 위의 리포지터리명과 동일한 이름의 폴더로 만들어지겠지

{% highlight bash %}
git clone https://github.com/{계정명}/{계정명}.github.io.git
cd {계정명}.github.io.git
{% endhighlight %}

*해당폴더에 올린게 없으니.. 비어있을테고.

#지킬설치
지킬을 sudo gem으로 설치한다
{% highlight bash %}
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
{% endhighlight %}

* 참고로 _config.yaml 은 수정해도 watch에서 못찾으므로 jekyll serve를 다시 실행해줘야 반영된다

#테마

##테마받기

dbyll이란 테마가 괜찮아 보였다. 특징은

* 카테고리 지원
* 태그지원
* 하얀색의 깔끔한 배경

URL
[dbyll테마](http://dbtek.github.io/dbyll/)

기존에 깔려있던 기본테마를 싹 지우고, 위의 URL에서 압축받은 것을 해당폴더에 넣는다

##설치시 문제
* paginate라는 플러그인을 사용하는 테마라서, 설치를 해줘야한다

{% highlight bash %}
sudo gem install pygments.rb
sudo gem install jekyll-paginate
{% endhighlight %}

* configuration에 아래 줄을 추가해줬다(첫번째줄에)

{% highlight bash %}
gems: [jekyll-paginate]
{% endhighlight %}

그리고 서버 실행해보면 테마가 짠 설정되어있음

{% highlight bash %}
jekyll serve --watch

//http://localhost:4000접속
{% endhighlight %}

