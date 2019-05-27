---
title: '[Hexo 테마] Next 댓글 사용하기(DISQUS)'
categories: Blog
tags:
  - blog
  - hexo
  - theme
  - next
  - disqus
date: 2019-05-27 18:59:52
---

[댓글 기능 추가하기](https://theme-next.org/docs/third-party-services/comments-and-widgets)
친절하게도 다양한 댓글 서비스를 연결할 수 있도록 준비되어 있다. 그 중에서 블로그 댓글로 많이 사용하는 `DISQUS`를 적용해 보도록 한다.

## DISQUS
1. 먼저 [DISQUS 홈페이지(https://disqus.com/)](https://disqus.com/)에 로그인한다.(가입 절차는 별도로 다루진 않는다)
2. (4번 항목의 페이지가 바로 나올 경우 바로 4번부터 진행하면 된다.) 우측 상단에 톱니바퀴 모양의 설정아이콘을 클릭해 나오는 메뉴에서 `Add Disqus To Site`를 선택
{% asset_img disqus1.jpg %}
3. 페이지 가장 하단의 `GET STARTED` 선택
{% asset_img disqus2.jpg %}
4. `I want to install Disqus on my site` 선택
{% asset_img disqus3.jpg %}
5. 항목을 채우고 `Create site` 선택
{% asset_img disqus4.jpg %}
6. 플랜 선택 화면, 무료버전은 `Basic`버전 선택
{% asset_img disqus5.jpg %}
7. 플랫폼 선택 화면, `I don't see my platform listed, install manually with Universal Code`를 선택
{% asset_img disqus6.jpg %}
8. 하단의 `configure` 선택
{% asset_img disqus7.jpg %}
9. 환경을 마무리하고 `Complete Setup` 선택
{% asset_img disqus8.jpg %}
10. `next/_config.yml` 파일의 `disqus` 환경 세팅
``` yaml
disqus:
  enable: true
  shortname: sams-web-story # DISQUS SITE의 URL 상단 주소 이름 참고. 예) https://sams-web-story.disqus.com
  count: true
  lazyload: false
```
11. 정상적으로 포스트 하단에 댓글 영역이 추가되었다.
{% asset_img disqus9.jpg %}