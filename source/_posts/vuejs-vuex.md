---
title: '[Vue.js] Vuex 알아보기'
categories: Vue.js
tags:
  - vue.js
  - vuex
  - javascript
  - store
  - state
date: 2019-05-24 19:41:43
---

Vue.js의 **상태관리 라이브러리**인 `Vuex`를 알아봅니다.

## 상태관리(State Management)의 필요성
Vue와 같은 컴포넌트 기반 프레임워크에서는 화면(page) 구성요소를 잘게 쪼개서 컴포넌트로 사용한다. `header`, `button`, `list`등의 작은 단위들이 컴포넌트가 되어서 한 화면에서 많은 컴포넌트를 사용하는데, 여기서 **각 컴포넌트 간의 통신이나 데이터 전달을 좀 더 유기적으로 관리할 필요성이 생긴다.**

이런 필요성에 의해 프레임워크에서는 저장소(store)라는 개념을 도입해 이 저장소를 각 컴포넌트에서 연결해 사용하는 식으로 상태관리를 한다.

Vue는 `Vuex`, React는 `Redux`나 `Flux`와 같은 상태관리 라이브러리를 사용한다.

## Vuex
- Vue.js 애플리케이션에 대한 **상태 관리 패턴 + 라이브러리**이다.
- 애플리케이션의 모든 컴포넌트에 대한 **중앙 집중식 저장소** 역할을 한다.
- 예측 가능한 방식으로 상태를 변경할 수 있다.
- Vue의 공식 [devtools 확장 프로그램](https://github.com/vuejs/vue-devtools)과 통합되어 **설정 시간이 필요 없는 디버깅** 및 **상태 스냅샷 내보내기/가져오기**와 같은 고급 기능을 제공한다.
- 다른 상태관리 패턴이나 라이브러리와 비교했을 때 Vue의 반응형(Reactivity) 체계를 효율적으로 활용하여 화면 업데이트가 가능하다는 차이점이 있다.

### 상태관리 패턴
3가지 상태관리 구성요소
- `상태(state)`: 앱을 작동하는 원본 소스(data)
- `뷰(view)`: 상태의 선언적 매핑(template)
- `액션(actions)`: 뷰에서 사용자 입력에 대해 반응적으로 상태를 바꾸는 방법(methods)
``` js
new Vue({
  // 상태(state)
  data () {
    return {
      count: 0
    }
  },
  // 뷰(view)
  template: `
    <div>{{ count }}</div>
  `,
  // 액션(actions)
  methods: {
    increment () {
      this.count++
    }
  }
})
```
위의 구성요소는 다음과 같이 동작한다.
<img src="/images/flow.png" alt="단방향 데이터 흐름" style="width:100%;max-width:500px;border:0 none;" />

### 문제 및 해결
위와같은 구조는 앱의 규모가 커질수록(**공통의 상태를 공유하는 여러 컴포넌트**가 있는 경우) 다음과 같은 문제가 발생한다.
- Vue의 기본 컴포넌트 통신방식(상위→하위)에서 **중간에 거쳐야 할 컴포넌트가 많아지거나**
- 이를 피하기 위해 Event Bus를 활용하여 **상하위 관계가 아닌 컴포넌트 간 통신 시 관리가 되지 않는 점**
이러한 문제들을 Vuex는 모든 데이터 통신을 한 곳(store)에서 중앙 집중식으로 관리하여 문제를 해결한다.

<img src="/images/vuex.png" alt="" style="width:100%;max-width:700px;border:0 none;" />

다음으로 Vuex를 사용하는 방법을 알아봅니다.

## 참고 링크
- [Vuex 공식 페이지](https://vuex.vuejs.org/kr/)
- [Captain Pangyo - Vuex 시작하기 1 - Vuex와 State](https://joshua1988.github.io/web-development/vuejs/vuex-start/)