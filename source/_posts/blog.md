---
title: Github Pages에 Blog 만들기
date: 2019-05-14 23:57:35
categories: Blog
tags: 
- blog
- github
- hexo
---
Github을 사용하고 있는 개발자들이 많이 사용하고 있는 Github Pages를 활용한 블로그를 만들어본다.
방법은 정적 사이트 생성기(Generator, 마크다운`.md`파일을 HTML`.html`파일로 변환해준다)를 활용하는데, 알려진 제너레이터로는 :
- jekyll
- hugo
- gatsby
- hexo

등이 있다.

나는 여기에서 [Hexo](https://hexo.io/ko/)를 사용해보도록 한다.

## 시작하기(Setup)
- [NodeJS](https://nodejs.org/ko/) 설치
- [Git](https://git-scm.com/) 설치
- [Github](https://github.com/)에 Repository 2개 생성  
  1. 배포(호스팅)용
  {% asset_img -6680207d-b25e-460f-93e1-b22211449438.jpg %}
  Tip : 저장소 이름은 `<github계정>.github.io`로 하면 편합니다.
  2. Hexo프로젝트 리소스 관리용
  {% asset_img -7f00bdeb-466d-4d5e-ad96-86c61804a5b1.jpg %}
  Tip : 저장소 이름은 상관없습니다.

**Hexo 시작**
``` bash
# Hexo cli 설치(글로벌)
$ npm install -g hexo-cli

# Hexo 초기화
$ hexo init myblog
$ cd myblog

# 내부 모듈 설치
$ npm install

# Github 저장소에 배포를 위한 hexo-deployer-git을 설치
$ npm install hexo-deployer-git --save

# 로컬 서버 시작(기본 http://localhost:4000)
$ hexo server
```

**Hexo 블로그 프로젝트 폴더 구조**
``` bash
├── _config.yml # Hexo 환경설정 파일
├── package.json # npm 환경 파일
├── scaffolds # 포스트 생성시 참조되는 레이아웃(page, post, draft) 파일들이 있는 폴더
├── source # 포스트(.md) 파일들이 저장되는 폴더
|   ├── _drafts # 임시 저장하는 포스트가 담기는 폴더. generate 명령어 실행시 제외 됨, publish 명령어로 source/_posts/ 폴더로 이동
|   └── _posts # 실제 포스트되는 파일이 담기는 폴더. generate 명령어로 public/ 폴더로 이동
├── public # source/ 의 포스트 파일들이 .html파일로 변환(generate)되어 저장되는 위치. clean 명령어로 지울 수 있고. deploy 명령어로 실제 서버에 배포된다.
└── themes # 블로그 테마가 설치되는 폴더
```

**프로젝트 리소스 관리를 위한 github commit & push**
``` bash
# 버전관리 폴더 생성 .git/
$ git init

# 파일 add
$ git add .

# 최초 commit
$ git commit -m "first commit"

# github 저장소에 remote
$ git remote add origin https://github.com/seungseop/seungseop.github.io.src.git

# github 저장소에 push
$ git push -u origin master
```

## 환경설정(Configuration)
`_config.yml` 파일 내부에서 환경 설정을 수정할 수 있습니다.
환경설정은 최소한 필요한 것만 다루고, 별도로 상세하게 다루도록 하겠다.
[공식문서 >](https://hexo.io/ko/docs/configuration)

**Site 정보**
``` yaml
## 웹 사이트의 제목. <title> 태그에 포함됨(테마에 따라 페이지에 노출)
title: Sam's
## 웹 사이트의 부제(테마에 따라 페이지에 노출)
subtitle: Web Story
## 웹 사이트에 대한 설명. <meta> 태그의 description 속성 값에 포함됨
description: Web Developer
## 작성자 이름
author: Sam
## 웹 사이트의 주 사용언어. <html> 태그의 lang 속성 값에 포함됨. 기본 값은 en
language: ko
## 웹 사이트에서 사용하는 timezone. 기본적으로 PC의 시간값을 사용.
## https://en.wikipedia.org/wiki/List_of_tz_database_time_zones에서 확인.
timezone: Asia/Seoul
```

**URL 정보**
``` yaml
## 이 웹 사이트의 URL
url: https://seungseop.github.io/
## 웹 사이트의 루트 디렉토리
root: /
## 게시글의 Permalinks 형식.
## https://hexo.io/ko/docs/permalinks 에서 확인.
permalink: :year/:month/:day/:title/
## Permalink 각 부분(segment)의 기본값
permalink_defaults:
```

**Deployment 정보**
``` yaml
deploy:
  type: git
  ## 자신의 Github의 Repository 정보를 입력
	repo: https://github.com/seungseop/seungseop.github.io
	branch: master
	message: 
```

## 포스트 작성하기
**new : 새 포스트 작성하기**
``` bash
# layout을 생략하면 환경설정 파일에 있는 'default_layout'값을 기준으로 생성된다.
$ hexo new [layout] <title>
```
생성하면 다음과 같은 경로에 Markdown(`.md`) 파일이 생성 된다.
``` bash
ㄴ source
  ㄴ _posts
    - <title>.md
```
생성된 파일의 기본 내용은 `scaffolds/`폴더 내에 있는 레이아웃 이름의 파일(템플릿)에서 가져온다.
``` md
---
title: {{ title }}
date: {{ date }}
categories: 
tags:
---

< 이곳에 Markdown으로 내용을 작성한다. >

```

## 배포하기(Deploy)
**배포 전에는 항상 `clean`명령어로 정적 리소스 폴더를 지워주는게 좋다.**
``` bash
$ hexo clean
```

**정적 리소스(`public/` 폴더) 생성하기**
``` bash
$ hexo generate
```

**배포하기**
``` bash
$ hexo deploy
# Generate와 Deploy를 동시에 할 수도 있다.
$ hexo deploy --generate
```

## 초안(_draft) 작성하기
Hexo는 게시글의 초안 작성은 `source/_drafts`폴더에서 할 수 있습니다.
환경 설정(`_config.yml`)의 `default_layout` 항목을 `post`가 아닌 `draft`로 설정한다면 (레이아웃 생략한)new 명령어로 draft상태의 게시글을 작성할 수 있습니다.

초안을 로컬 서버에서 보고 싶다면 `--draft`옵션을 주면됩니다.
``` bash
$ hexo server --draft
```
매번 `--draft`옵션을 주기 싫다면 환경 파일의 `render-drafts` 항목을 `true`로 변경해주세요.
``` yaml
render_drafts: true
```

작성된 초안은 `source/_posts`폴더로 게시 할 수 있습니다.
``` bash
$ hexo publish [layout] <filename>
```

- - -
배포가 완료되면 설정했던 URL 주소[(https://seungseop.github.io/)](https://seungseop.github.io/)로 접근해서 정상적으로 반영이 되었는지 확인한다.