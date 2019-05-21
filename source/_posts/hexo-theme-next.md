---
title: Hexo 테마 - Next
categories: Blog
tags:
  - blog
  - hexo
  - theme
  - next
date: 2019-05-16 16:26:32
---

{% asset_img image1.png %}

## 설치하기(Installation)
**1. 테마 설치**
```bash
$ cd [myBlog] # 내 블로그(Hexo Project) 폴더로 이동
$ git clone https://github.com/theme-next/hexo-theme-next themes/next
```

**2. Hexo 환경파일(`_config.yml`)의 theme 속성 변경**
``` yaml
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: next
```

**3. Hexo 서버 재시작**
```bash
hexo clean
hexo s # hexo server
```

## 테마 환경 설정
**테마 환경파일 위치 : `themes/next/_config.yml`**
  - 아카이브(Archive) 내에 응원메세지(cheers) 비활성화 하기.
    (한국어로 "음..! 총 n개의 포스트 포스트를 마저 작성하세요"라는 메세지가 출력되는데 마치 내 포스트가 전부 미완성인 것만 같다.)
  ``` yaml
  # Enable "cheers" for archive page.
  cheers: false
  ```
  `themes/next/languages/ko.yml`파일에 있는 해당 문구를 변경해도 된다.

  - 공통 아이콘
  환경 파일 내부에서 사용되는 아이콘의 이름은 모두 `font-awesome(4.7버전)`을 사용한다. 각 아이콘의 이름은 다음 링크를 참고한다.
  [font-awesome (https://fontawesome.com/v4.7.0/icons/)](https://fontawesome.com/v4.7.0/icons/)

## 기타
**1. 메뉴항목(페이지) 추가하기**
  - 공통 : 설정파일에 원하는 메뉴항목을 추가해준다. 각 항목은 `Key: value` 쌍으로 이루어져있으며, 'Key'는 해당 `메뉴의 이름`, 'value'는 URL `params값`과 보여지는 `아이콘 이름`을 설정할 수 있다. 두 개의 값은 `||`로 구분한다.
  ``` yaml
  # themes/next/_config.yml
  menu:
    home: / || home
    about: /about/ || user
    tags: /tags/ || tags
    categories: /categories/ || th
    archives: /archives/ || archive
    schedule: /schedule/ || calendar
    sitemap: /sitemap.xml || sitemap
    commonweal: /404/ || heartbeat
  ```
  {% asset_img etc1.jpg %}
  - 카테고리
    1) `categories` 항목을 추가해주고, 다음을 입력하여 페이지를 추가해준다.
    ``` bash
    $ hexo new page categories
    ```
    2) 추가된 파일(`/source/categories/index.md`)을 다음과 같이 수정해준다.
    ``` md
    ---
    title: categories
    date: YYYY-MM-DD HH:mm:ss
    type: "categories"
    comments: false
    ---
    ```
    3) 포스트 작성 시 상단 헤드 내용에 `categories` 항목을 추가 작성해준다.
    ``` md
    ---
    title: Hexo 테마 - Next
    categories: Blog
    tags:
    - blog
    - hexo
    - theme
    - next
    ---
    ```
    (TIP: `/scaffolds/`폴더 내부 파일에 항목을 추가해주면 `hexo new`명령어로 포스트 작성 시 항목이 자동으로 붙는다.)



  - `tags`
  ``` yaml
  # themes/next/_config.yml

  ```

### 참고 링크
- [Hexo Next Github](https://github.com/theme-next/hexo-theme-next)
- [chentging Blog](https://to.ly/1z48Q)