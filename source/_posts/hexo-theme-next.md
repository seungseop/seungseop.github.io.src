---
title: "[Hexo 테마] Next"
categories: Blog
tags:
  - blog
  - hexo
  - theme
  - next
date: 2019-05-16 16:26:32
---
데모이자 도큐먼트 페이지 보자마자 너무 이뻐서 선택하게된 테마, 도큐먼트도 상세하게 잘 설명되어있어 마음에 쏙 들었다.

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

### 메뉴항목(페이지) 추가하기
#### 공통 : 설정파일에 원하는 메뉴항목을 추가해준다. 각 항목은 `Key: value` 쌍으로 이루어져있으며, 'Key'는 해당 `메뉴의 이름`, 'value'는 URL `params값`과 보여지는 `아이콘 이름`을 설정할 수 있다. 두 개의 값은 `||`로 구분한다.
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

#### 카테고리
1) 환경파일(`themes/next/_config.yml`)의 `categories` 항목을 추가해주고, 다음을 입력하여 페이지를 추가해준다.
``` bash
$ hexo new page categories
```
2) 추가된 파일(`/source/categories/index.md`)을 다음과 같이 수정해준다.
``` md
---
title: 카테고리(categories)
date: 2019-05-16 10:10:40
type: "categories"
comments: false
---
```
3) 포스트 작성 시 상단 헤드 내용에 `categories` 항목을 추가 작성해준다.
``` md
---
title: Hexo 테마 - Next
categories: Blog
...
---
```
(TIP: `/scaffolds/`폴더 내부 파일에 항목을 추가해주면 `hexo new`명령어로 포스트 작성 시 항목이 자동으로 붙는다.)

#### `tags`
1) 환경파일(`themes/next/_config.yml`)의 `tags` 항목을 추가해주고, 다음을 입력하여 페이지를 추가해준다.
``` bash
$ hexo new page tags
```
2) 추가된 파일(`/source/tags/index.md`)을 다음과 같이 수정해준다.
``` md
---
title: 태그(tags)
date: 2019-05-16 10:10:40
type: "tags"
comments: false
---
```
3) 포스트 작성 시 상단 헤드 내용에 `tags` 항목을 추가 작성해준다. 태그들은 `하이픈(-)의 리스트 형태`로 구분한다.
``` md
---
title: Hexo 테마 - Next
tags:
- blog
- hexo
- theme
- next
...
---
```
(TIP: `/scaffolds/`폴더 내부 파일에 항목을 추가해주면 `hexo new`명령어로 포스트 작성 시 항목이 자동으로 붙는다.)

### Widgets
- [댓글 기능 추가하기](/2019/05/27/hexo-theme-next-disqus/)

## 참고 링크
- [Hexo Next Github](https://github.com/theme-next/hexo-theme-next)
- [chentging Blog](https://chentging.github.io/2018/05/14/hexo%EF%BC%9A%EF%BC%88%E4%B8%89%EF%BC%89hexo-Next-%E4%B8%BB%E9%A2%98%E4%B8%8B%E8%BD%BD%E5%92%8C%E9%85%8D%E7%BD%AE/)