---
title: Hexo 테마 - Next
tags:
- blog
- hexo
- theme
- next
---
{% asset_img image1.png %}

## 설치하기(Installation)
1. 테마 설치
```bash
$ cd [myBlog] # 내 블로그(Hexo Project) 폴더로 이동
$ git clone https://github.com/theme-next/hexo-theme-next themes/next
```

2. `_config.yml` 파일의 theme 속성 변경
```yaml
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: next
```

3. Hexo 서버 재시작
```bash
hexo clean
hexo s # hexo server
```

## 테마 환경 설정(`themes/next/_config.yml`)
  - ㅁ
  ```yaml
  # themes/next/_config.yml

  ```

## 기타
1. 메뉴(페이지) 추가하기
  - `공통` : 원하는 메뉴항목을 추가해준다.
  ```yaml
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

  - `tags`
  ```yaml
  # themes/next/_config.yml

  ```


### 참고 링크
- [Hexo Next Github](https://github.com/theme-next/hexo-theme-next)
- [chentging Blog](https://to.ly/1z48Q) (※ 중국어 주의)