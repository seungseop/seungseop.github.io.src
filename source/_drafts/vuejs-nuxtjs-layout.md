---
title: vuejs-nuxtjs-layout
categories:
tags:
---
## layout 프로퍼티
`layouts 디렉토리`의 모든 파일(최상위 레벨)은 **페이지 컴포넌트**의 `layout 프로퍼티`를 사용하여 접근가능한 사용자 정의 layout을 만들 수 있습니다.

- 타입: `String` 또는 `Function` (기본값: `'default'`)

페이지 컴포넌트에서 사용할 레이아웃을 정의하기 위해서 `layout 키`를 정의하세요.

``` js
export default {
  layout: 'blog',
  // 또는
  layout (context) {
    return 'blog'
  }
}
```

예를 들어, Nuxt.js는 페이지 컴포넌트의 layout으로 layouts/blog.vue을 포함할 것입니다.

어떻게 동작하는지 데모 비디오를 확인해주세요.

nuxt.js의 layouts가 어떻게 동작하는지 이해하기 위해 layout 문서를 확인하세요.

## 참고 링크
- [NuxtJS - layout](https://ko.nuxtjs.org/api/pages-layout/)
- [NuxtJS - Views](https://ko.nuxtjs.org/guide/views/)