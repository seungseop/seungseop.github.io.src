---
title: Vue.js
categories: Vue.js
tags:
  - javascript
  - framework
  - vue.js
date: 2019-05-20 16:30:51
---

<img src="/images/vue-js_logo.png" width="200" style="border:0 none;" />

## [Vue.js](https://kr.vuejs.org/v2/guide/index.html)
Vue.js는 개발자 '에반 유(Evan You)'가 MVVM 패턴(애플리케이션 개발 디자인 패턴)에서 영감을 받아 만들었으며, MVVM 패턴 중 ViewModel(VM) 부분의 기능을 담당하는 프레임워크입니다.

### MVVM 패턴이란?


### Vue.js 특징
- 가상 DOM을 사용합니다.
- 컴포넌트를 제공합니다.
- 뷰에만 집중을 하고 있고, 라우터, 상태관리를 위해선 써드파티 라이브러리를 사용합니다.

### MVVM 패턴
{% asset_img vue-js1.jpg %}

#### View
``` html
<div id="simple">
	<h2> {{ message }} </h2>
</div>
```

#### View Model
``` js
var simple = new Vue({
  ...
})
```

#### Model
``` js
var model = {
	message: "..."
}
```

### `｛{ message }｝` : 보간법(Interpolation), 콧수염 표현식(Mustache Expression)
HTML 요소에는 `<div>｛{ message }｝</div>`와 같이 괄호로 감싼 템플릿 표현식을 사용해 선언적으로 HTML DOM에 데이터를 렌더링합니다.

### `<template>`태그
렌더링 내용에는 포함되지 않는 태그. 단지 요소들을 그룹으로 묶어주기 위한 용도로만 사용합니다.


## 참고 링크
- [Vue.js](https://kr.vuejs.org/v2/guide/index.html)
- [CaptainPangyo - Vue.js 입문서 - 프론트엔드 개발자를 위한](https://joshua1988.github.io/web-development/vuejs/vuejs-tutorial-for-beginner/)
- [VELOPERT.LOG - [Vue.JS 2.0] 소개 및 시작하기](https://velopert.com/3007)
- [TOAST Meetup - 자바스크립트 프레임워크 소개 3 - Vue.js](https://meetup.toast.com/posts/99)