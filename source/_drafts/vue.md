---
title: vue
tags:
---
Vue인스턴스 내부 데이터를 동적으로 추가하고 삭제할때에는 vue.set() / vue.delete()를 사용해야한다.
=> 객체 프로퍼티를 추가하듯이 데이터를 추가한다면 그 데이터는 Reactive(반응형) 데이터가 아니다.(Vue인스턴스가 이를 감지하지 못함)

Vue인스턴스 내부의 속성 중 앞에 $이 붙는 속성은 변경해도되는 public한 속성이고, _가 붙는 속성은 private한 속성이다.
=> private 속성은 변경하면 안됨. Vue가 동작하며 그 값들을 언제든 변경할 수 있기 때문.

methods의 function을 호출할 때 다음과 같이 (@click="funcName('test', $event)") $event로 이벤트 객체를 인자의 위치를 지정해서 넘길 수 있다.

부모 컴포넌트에서 자식 컴포넌트로 props를 넘길 때 배열형태로( props: ['newProps'] ) 넘겨 주는 것 보다는,
props: {
  newProps: {
    type: String,
    required: false,
    default: '' // required가 false인 경우 default 값을 설정할 수 있다.
  }
}
처럼 props의 형태를 지정해주는 것을 추천.