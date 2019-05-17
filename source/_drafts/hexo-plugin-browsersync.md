---
title: Hexo live-reload 플러그인(hexo-browsersync)
categories: Hexo
tags:
- hexo
- plugin
- live-reload
- browsersync
---
Hexo를 이용해 Markdown(.md)으로 글 포스팅을 하다보면 코딩하는 것과 비슷한 느낌을 받는다.(포스팅을 VScode로 해서그런가...)
프론트 페이지 작업을 하다보면, 저장할 때마다 Refresh(F5)를 해주는게 너무 귀찮은일이 아닐 수 없다.
이런 불편함을 해소하기 위해 나온게 live-reload(browsersync) 기능인데, Hexo에도 이런 기능을 하는 플러그인이 있길래 설치해본다.

## 설치하기(Installation)
``` bash
$ npm install hexo-browsersync --save
$ hexo server --draft --open # 서버 재시작
```

## 실행하기
모듈을 설치하고 그냥 똑같이 `hexo server` 명령어를 통해 실행하면 함께 시작된다.
``` bash
$ hexo server --draft --open
INFO  Start processing
[Browsersync] Access URLs:
 ----------------------------------
          UI: http://localhost:3001
 ----------------------------------
 UI External: http://localhost:3001
 ----------------------------------
INFO  Hexo is running at http://localhost:4000 . Press Ctrl+C to stop.
```
시작하고 페이지에 들어가보면, 아래와 같이 우측상단에 `Browsersync: connected`라는 연결메세지가 나타난다.
{% asset_img hexo-plugin-browsersync2.jpg %}

연결된 후 글을 수정하고 저장을 하면 다음과 같이 출력되면서 페이지가 자동으로 새로고침된다.
``` bash
[Browsersync] Reloading Browsers...
[Browsersync] Reloading Browsers...
[Browsersync] Reloading Browsers...
```

## 문제
{% asset_img hexo-plugin-browsersync1.jpg %}
일부 페이지(홈)가 정상적으로 렌더링되지 않는 현상이 있다.