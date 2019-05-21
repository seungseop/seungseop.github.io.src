---
title: Vue.js - 디렉티브(directive)
date: 2019-05-21 16:29:50
categories: Vue.js
tags:
  - javascript
  - framework
  - vue.js
---

# [디렉티브(directive)](https://kr.vuejs.org/v2/api/#%EB%94%94%EB%A0%89%ED%8B%B0%EB%B8%8C)
디렉티브는 속성명 앞에 `v-`로 시작하는 프리픽스가 붙는 특수한 속성으로 새로운 기능을 제공한다.
디렉티브의 속성 값은 단일 **javscript 표현식**이다.

## 1. v-text(== ｛{ ... }｝) / v-html
HTML 요소 내부에 내용을 렌더링 하기 위한 방식 `v-text`는 javascript의 `innerText`와 같고, `v-html`은 `innerHTML`와 같이 동작한다.
``` html
<span v-text="msg"></span>
<-- '<span>{{msg}}</span>'와 같이 동작합니다. -->

<span></span>
```

## v-bind(`:`)
요소 객체의 속성들을 바인딩하기 위해 사용한다.
``` html
<img v-bind:src="imagePath" /> <-- 안의 imagePath는 변수이다. -->
<img :src="imagePath" /> <-- ':'만 써서 축약해서 사용이 가능하다. -->
```

## v-model
`v-bind`는 단방향 데이터 바인딩이라면, `v-model`은 양방향