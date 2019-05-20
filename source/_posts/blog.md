---
title: Github Pages에 Blog 만들기
date: 2019-05-14 23:57:35
categories: Blog
tags: 
- blog
- github
- hexo
---
# 시작하기(Setup)
- [NodeJS](https://nodejs.org/ko/) 설치
- [Git](https://git-scm.com/) 설치
- [Github](https://github.com/)에 Repository 2개 생성  
  1. 배포(호스팅)용
  {% asset_img -6680207d-b25e-460f-93e1-b22211449438.jpg %}
  Tip : 저장소 이름은 `<github계정>.github.io`로 하면 편합니다.
  2. Hexo프로젝트 리소스 관리용
  {% asset_img -7f00bdeb-466d-4d5e-ad96-86c61804a5b1.jpg %}
  Tip : 저장소 이름은 상관없습니다.

## [Hexo](https://hexo.io/ko/) 시작
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

# 로컬 서버 시작
$ hexo server
```

- Hexo 블로그 프로젝트 폴더 구조
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

### 프로젝트 리소스 관리를 위한 github commit & push
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