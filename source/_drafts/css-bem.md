---
title: BEM(Block Element Modifier) 방법론
categories: CSS
tags:
- StyleSheet
- CSS 방법론
- BEM
---
프로젝트 작업 시 CSS `class`를 작명할 때 정해둔 기준이 없어 뭔가 기준을 정하고자 `CSS 방법론`을 알아본다.

먼저 CSS 방법론을 사용하는 이유는,
- 쉬운 유지보수가 가능하다.
- 재사용이 가능하다.
- 쉽게 확장이 가능하다.

CSS 방법론에는 SMASS, BEM, OOCSS 등이 있지만 그 중에서도 `BEM`을 적용하기로 했다. 이유는 BEM은 Sass에서 사용할 때 하위 요소로 내려갈 때마다 중복되는 이름을 `&`로 생략할 수 있는게 편했기 때문이다.

## BEM(Block Element Modifier)
<img src="/images/bem_logo.png" width="200" style="border:0 none;" />

BEM은 이름 그대로 블록(Block) / 요소(Element) / 수식어(Modifier)를 구분하고 이를 연결한 형태로 작명하는 `block__element--modifier`, `block--modifier`와 같은 형태를 띈다.

**작명 규칙(Naming Convention)**
- 개발, 디버깅, 유지보수를 위하여 CSS 선택자의 이름을 가능한 한 명확하게 만드는 것이 목표이다.
- 소문자, 숫자 만을 이용해서 작명한다.
- 여러단어의 조합은 하이픈(-)으로 연결하여 작명한다.

**블록(Block)**
- 재사용 할 수 있는 기능적으로 독립적인 페이지 구성 요소(예로 하나의 컴포넌트 단위)
- HTML에서 블록은 class 속성으로 표시된다.
- 형태(red, big)가 아닌 목적(menu, button)에 맞게 결정해야 한다.
- 블록은 환경에 영향을 받지 않아야 한다. 즉, 여백이나 위치를 설정하면 안된다.
- 태그, id 선택자를 사용하면 안된다.
- 블록은 서로 중첩해서 작성할 수 있다.
- 예) header, menu, search-form ...

**요소(Element)**
- 블록이 포함하고 있는 하나의 조각(`특정 기능`)
- `block__element` 형태로, 블록 뒤에 두개의 언더바(__)로 연결
- 형태(red, big)가 아닌 목적(item, text, title)에 맞게 결정해야 한다.
- 예)
``` css
.header__logo {property: value;}
.header__tagline {property: value;}
.header__searchbar {property: value;}
.header__navigation {property: value;}
```
- 요소는 중첩해서 작성 할 수 있다.
- 요소는 블록의 부분으로만 사용할 수 있고 다른 요소의 부분으로는 사용할 수 없다.
- 모든 블록에서 요소는 필수가 아닌 선택적으로 사용한다. 즉, 블록안에 요소가 없을 수도 있다.
- 예) menu__item, header__title ...

**수식어(Modifier)**
- 블록이나 요소의 `모양(color, size..)`, `상태(disabled, checked..)`를 정의
- `block__element--modifier`, `block--modifier` 형태로 사용(더블 하이픈)
- 수식어의 `블리언 타입`과 `키-벨류` 타입이 있다.


### 참고 링크
- [https://medium.com/witinweb/css-%EB%B0%A9%EB%B2%95%EB%A1%A0-1-bem-block-element-modifier-1c03034e65a1](https://medium.com/witinweb/css-%EB%B0%A9%EB%B2%95%EB%A1%A0-1-bem-block-element-modifier-1c03034e65a1)
- [https://webclub.tistory.com/263](https://webclub.tistory.com/263)
- [https://a-tothe-z.tistory.com/2](https://a-tothe-z.tistory.com/2)