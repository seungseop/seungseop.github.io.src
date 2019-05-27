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
여기서는 Vue.js의 **상태관리 라이브러리**인 `Vuex`를 알아봅니다.

## 상태관리(State Management)의 필요성
Vue와 같은 **컴포넌트 기반 프레임워크**에서는 화면(page)을 `header`, `button`, `list`등의 많은 컴포넌로 잘게 쪼개서 컴포넌트로 사용하는데, 여기서 각 컴포넌트 간의 **통신이나 데이터 전달**을 좀 더 **유기적으로 관리할 필요성**이 생기게됩니다.

이러한 필요성에 의해 생겨난 **상태관리 라이브러리**는 각 컴포넌트가 **저장소(store)**라는 곳을 연결해 사용하는 식의 상태관리를 합니다.

Vue는 `Vuex`, React는 `Redux`나 `Flux`와 같은 상태관리 라이브러리를 사용하고 있습니다.

## Vuex
- Vue 애플리케이션에 대한 **상태 관리 패턴 + 라이브러리**입니다.
- 애플리케이션의 모든 컴포넌트에 대한 **중앙 집중식 저장소** 역할을 합니다.
- **예측 가능한 방식**으로 상태를 변경할 수 있습니다.
- Vue의 공식 [devtools 확장 프로그램](https://github.com/vuejs/vue-devtools)과 통합되어 **설정 시간이 필요 없는 디버깅** 및 **상태 스냅샷 내보내기/가져오기**와 같은 고급 기능을 제공합니다.
- 다른 상태관리 패턴이나 라이브러리와 비교했을 때 Vue의 **반응형(Reactivity)** 체계를 효율적으로 활용하여 화면 업데이트가 가능하다는 차이점이 있습니다.

### 상태관리 패턴
상태관리 구성요소 세가지(상태, 뷰, 액션)
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
위의 구성요소는 다음과 같이 동작합니다.
<img src="/images/flow.png" alt="단방향 데이터 흐름" style="width:100%;max-width:500px;border:0 none;" />

### 문제 및 해결
위와같은 구조는 앱의 규모가 커질수록(**공통의 상태를 공유하는 여러 컴포넌트**가 있는 경우) 다음과 같은 문제가 발생합니다.
- Vue의 기본 컴포넌트 통신방식(상위→하위)에서 **중간에 거쳐야 할 컴포넌트가 많아지거나**
- 이를 피하기 위해 **Event Bus**를 활용하여 **상하위 관계가 아닌 컴포넌트 간 통신 시 관리가 되지 않는 점**
이러한 문제들을 `Vuex`는 모든 데이터 통신을 한 곳(저장소, store)에서 **중앙 집중식으로 관리**하여 문제를 해결합니다.

<img src="/images/vuex.png" alt="" style="width:100%;max-width:700px;border:0 none;" />

### 저장소(store) 사용하기
**"저장소(store)"**는 기본적으로 애플리케이션 **상태**를 보유하고있는 컨테이너 입니다.
- Vuex store는 **반응형(Reactivity)** 입니다. Vue 컴포넌트는 상태를 검색할 때 저장소의 상태가 변경되면 효율적으로 대응하고 업데이트 합니다.
- 저장소의 **상태를 직접 변경할 수 없습니다**. 저장소의 상태를 변경하는 유일한 방법은 명시적인 **커밋(Commit)**을 이용한 변이 입니다. 이렇게하면 모든 상태에 대한 추적이 가능한 기록이 남을 수 있으며 툴을 사용하여 앱을 더 잘 이해할 수 있습니다.

Vuex를 [설치](https://vuex.vuejs.org/kr/installation.html)한 후 저장소를 만들어 봅니다.
``` js
// 모듈 시스템을 사용하는 경우 Vue.use(Vuex)를 먼저 호출해야합니다.

const store = new Vuex.Store({
  state: {
    count: 0
  },
  mutations: {
    increment (state) {
      state.count++
    }
  }
})
```

state 객체에 `store.state`로 접근하여 `store.commit` 메소드로 상태 변경을 트리거 할 수 있습니다.
``` js
store.commit('increment');

console.log(store.state.count) // 1
```
`store.state.count`를 직접 변경하는 대신 변이를 수행하는 이유는 **명시적으로 추적을 하기 때문**입니다. 이 간단한 규칙에 따라 의도를보다 명확하게 표현할 수 있으므로 코드를 읽을 때 상태 변화를 더 잘 지켜볼 수 있습니다. 또한 모든 변이를 기록하고 상태 스냅샷을 저장하거나 시간 흐름에 따라 디버깅을 할 수 있는 도구를 제공합니다.

컴포넌트 안에서 저장소 상태를 사용하는 것은 단순히 계산된 속성 내에서 상태를 반환하는 것입니다. 변경을 트리거하는 것은 컴포넌트 메소드에서 변경을 커밋하는 것을 의미합니다.

## 참고 링크
- [Vuex 공식 페이지](https://vuex.vuejs.org/kr/)
- [Captain Pangyo - Vuex 시작하기 1 - Vuex와 State](https://joshua1988.github.io/web-development/vuejs/vuex-start/)