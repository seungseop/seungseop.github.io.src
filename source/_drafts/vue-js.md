---
title: Vue.js
categories: Vue.js
tags:
- javascript
- framework
- vue.js
---
<img src="/images/vue-js.png" width="200" style="border:0 none;" />

# [Vue.js](https://kr.vuejs.org/v2/guide/index.html)
'에반 유(Evan You)'라는 개발자가 만든 Front-end Javscript Framework.
Vue.js는 Application 개발 디자인 패턴 중 MVVM 패턴에서 영감을 받아 그 중 ViewModel(VM)과 같은 부분을 담당하는 프레임워크이다.

## MVVM 패턴
{% asset_img vue-js1.png %}

### View
``` html
<div id="simple">
	<h2> {{ message }} </h2>
</div>
```

### View Model
``` js
var simple = new Vue({
  ...
})
```

### Model
``` js
var model = {
	message: "..."
}
```

## `｛{ message }｝` : 보간법(Interpolation), 콧수염 표현식(Mustache Expression)
HTML 요소에는 `<div>｛{ message }｝</div>`와 같이 괄호로 감싼 템플릿 표현식을 사용해 선언적으로 HTML DOM에 데이터를 렌더링합니다.

## `<template>`태그
렌더링 내용에는 포함되지 않는 태그. 단지 요소들을 그룹으로 묶어주기 위한 용도로만 사용합니다.