---
layout: post
title: 지킬 세팅하기
categories:
- jekyll
---

#github 만들기

## github 가입후, repository명 만들기

* github 가입을 한 후에, respository를 다음과 같은 형식으로 만들어야한다

~~~ bash
{계정명}.github.io
~~~

그럼 클론을 받으면 위의 리포지터리명과 동일한 이름의 폴더로 만들어지겠지

~~~ bash
git clone https://github.com/{계정명}/{계정명}.github.io.git
cd {계정명}.github.io.git
~~~

*해당폴더에 올린게 없으니.. 비어있을테고.

#지킬설치
지킬을 sudo gem으로 설치한다

~~~ bash
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

naringu이란 테마가 괜찮아 보였다. 특징은

* 카테고리 지원
* 코드블럭

URL

[Naringu 테마다운](https://github.com/ariestiyansyah/naringu)


기존에 깔려있던 기본테마를 싹 지우고, 위의 URL에서 압축받은 것을 해당폴더에 넣는다

##설치시 문제
* paginate라는 플러그인을 사용하는 테마라서, 설치를 해줘야한다
* redcarpet도 설치를 해주어야한다

~~~ bash
sudo gem install pygments.rb
sudo gem install jekyll-paginate
sudo gem install redcarpet
~~~

* configuration에 아래 줄을 추가해줬다(첫번째줄에)

~~~ javascript
gems: [jekyll-paginate]
~~~

* relative_permalinks 를 해지해준다

~~~ javascript
relative_permalinks: false
~~~

그리고 서버 실행해보면 테마가 짠 설정되어있음

~~~ bash
jekyll serve --watch

//http://localhost:4000접속
~~~

## disqus 연동
댓글 달수 있는 disqus 사이트에 회원가입 후, 서비스를 만든다.
https://publishers.disqus.com/

* Unversial Install 눌러서 아래와 같은 코드가 이미 _includes/comments.html에 있으므로
* _config.yml에서 disqus에 나의 서비스명인 **swoosblog** 를 넣어주었다.

~~~
<div id="disqus_thread"></div>
<script type="text/javascript">
    /* * * CONFIGURATION VARIABLES * * */
    var disqus_shortname = '{{ site.disqus }}';

    /* * * DON'T EDIT BELOW THIS LINE * * */
    (function() {
        var dsq = document.createElement('script'); dsq.type = 'text/javascript'; dsq.async = true;
        dsq.src = '//' + disqus_shortname + '.disqus.com/embed.js';
        (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(dsq);
    })();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript" rel="nofollow">comments powered by Disqus.</a></noscript>

<script type="text/javascript">
    /* * * CONFIGURATION VARIABLES * * */
    var disqus_shortname = '{{ site.disqus }}';

    /* * * DON'T EDIT BELOW THIS LINE * * */
    (function () {
        var s = document.createElement('script'); s.async = true;
        s.type = 'text/javascript';
        s.src = '//' + disqus_shortname + '.disqus.com/count.js';
        (document.getElementsByTagName('HEAD')[0] || document.getElementsByTagName('BODY')[0]).appendChild(s);
    }());
</script>
~~~

이메일 인증까지 하면 완료.


## Google Analytics 연동

* 구글어날러틱스 서비스를 추가하고,

* _includes/analytics.html 에 아래의 코드로 추가하였다.

~~~
<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
            (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
          m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-72227668-1', 'auto');
  ga('send', 'pageview');

</script>
~~~