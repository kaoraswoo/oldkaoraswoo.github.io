---
layout: post
title: jekyll로 만든 블로그 사이트 구글검색가능하게하기
categories: [jekyll]
tags: [server,jekyll]
fullview: true
comments: true
---

#왜 사이트맵을 생성해야하나?
구글에서 검색이 가능하게 하기 위해서, [Webmaster tool](https://www.google.com/webmasters/tools) 에 속성을 추가한 후에, 해당사이트에 대한 정보를 구글측에 알리기 위해서 필요하다.

## 속성추가 및 인증

* 처음 내가 만든 웹사이트의 속성을 추가하면, 구글에서 제공한 html을 다운로드 받을 수 있다. (ex: google2f231e0b5ab295ab.html)
* 해당파일을 나의 사이트에 올리고, 확인을 누르면, 인증이 완료된다.

## 사이트맵파일 작성

* 이제 현재까지 생성된 모든 포스트들의 대해서 사이트맵을 작성해야하는데, 다음과 같은 형식을 하면, 검색이 가능하다.

* 단, _config.yaml에 url 설정을 넣어서, sitemap.xml에서 site.url 변수값을 사용할 수 있게 한다.

~~~
url: http://kaoraswoo.github.io
~~~

* sitemap.xml 내용

[이 사이트를 참조한다](http://joelglovier.com/writing/sitemaps-for-jekyll-sites/)


## 구글에 사이트맵 제출
* 웹마스터 툴에서, sitemap 테스트/제출을 눌러서, 내가 올린 sitemap.xml이 제대로 동작하는지 확인한 후, 제출한다.

```
http://kaoraswoo.github.io/sitemap.xml
```

## 그 외에 해야할것?
* 향후정리 필요