---
title: BEM(Block Element Modifier) 방법론
categories: CSS
tags:
  - CSS
  - CSS 방법론
  - BEM
date: 2019-05-23 18:15:34
---

프로젝트 작업할 때 CSS 선택자 즉, `class`를 작명하는데 기준이 없어 사람마다 다 다른 중구난방한 이름들을 볼 때마다 매우 답답한 게 있었는데요, 이번 기회에 이를 정리하고자 `CSS 방법론`을 알아보기로 합니다.

먼저 CSS 방법론을 사용하는 이유로는,
- 쉬운 유지 보수가 가능하다.
- 재사용이 가능하다.
- 쉽게 확장이 가능하다.
와 같은 게 있다고 합니다.

CSS 방법론에는 SMASS, BEM, OOCSS 등이 있지만 그중에서도 `BEM`을 적용해 보기로 했습니다. 그 이유는 BEM은 Sass나 Less에서 사용할 때 하위 요소로 내려갈 때마다 중복되는 이름을 `&`로 생략하여 편하게 작성할 수 있기 때문입니다.
``` scss
.block {
  /* CSS declarations for `.block` */
  &__element { /* CSS declarations for `.block__element` */ }
  &--modifier {
    /* CSS declarations for `.block--modifier` */
    &__element { /* CSS declarations for `.block--modifier__element` */ }
  }
}
```

## BEM(Block Element Modifier)
<img src="/images/bem_logo.png" alt="BEM" width="200" style="border:0 none;" />

BEM은 "Yandex"라는 회사에서 개발한 방법론으로, BEM 이름 그대로 블록(Block) / 요소(Element) / 수식어(Modifier)로 구분하고 이를 두 개의 언더 스코어(\__)나 하이픈(\--)으로 연결한 형태로 작명하는(`block__element--modifier`, `block--modifier`) 형태를 띱니다.

### 작명 규칙(Naming Convention)
- 개발, 디버깅, 유지보수를 위하여 CSS 선택자의 이름을 가능한 한 **명확하게** 만드는 것이 목표이다.
- **영어 소문자**, **숫자**만을 이용한다.
- 여러단어의 조합은 **하이픈(-)**으로 연결한다.

### 블록(Block)
- 페이지 구성 요소 중 **재사용** 할 수 있고, 기능적으로 **독립적인**. 즉, 하나의 **컴포넌트** 요소이다.
- HTML에서 블록은 **class 속성**으로 표시한다.
- 형태(red, big)가 아닌 **목적(menu, button)**에 맞게 결정한다.
- 블록은 환경에 영향을 받지 않아야 한다. 즉, 여백이나 위치를 설정하면 안된다.
- 태그명, id 선택자를 사용하면 **안된다.**
- 블록은 **서로 중첩**해서 작성할 수 있다.
예) 
``` html
<div class="header">
  <div class="menu">
    <div class="search-form">
    </div>
  </div>
</div>
```

### 요소(Element)
- **블록이 포함**하고 있는 하나의 조각(**특정 기능**)이다.
- `block__element` 형태로, 블록 뒤에 두개의 언더 스코어(\__)로 연결한다.
- **형태(색상, 크기)**가 아닌 **목적(item, text, title)**에 맞게 결정해야 한다.
예)
``` css
.header__logo {property: value;}
.header__tagline {property: value;}
.header__searchbar {property: value;}
.header__navigation {property: value;}
```
- 요소는 **중첩해서 작성** 할 수 있다.
- 요소는 **블록의 부분으로만 사용**할 수 있고 다른 요소의 부분으로는 사용할 수 없다.
- 모든 블록에서 **요소는 필수가 아닌 선택적으로 사용**한다. 즉, 블록안에 요소가 없을 수도 있다.
예) menu__item, header__title ...

### 수식어(Modifier)
- 블록이나 요소의 **모양(color, size..)**, **상태(disabled, checked..)**를 정의한다.
- `block__element--modifier`, `block--modifier` 형태로, 블록이나 요소 뒤에 두개의 하이픈(--)으로 연결한다.
- 수식어는 **불리언 타입(boolean)**과 **키-벨류** 타입이 있다.
- **불리언 타입**: 수식어가 있으면 값이 true라고 가정한다. (`from__button--disabled`)
- **키-벨류 타입**: 키, 벨류를 하이픈으로 연결하여 표시한다. (`color-red`, `theme-ocean`)
- 수식어는 **단독으로 사용할 수 없다**. 즉, 기본 **블록과 요소에 추가하여 사용**해야 한다. (`class="block__element block__element--modifier"`)

### 혼합사용(Mix)
- `block1`, `block2__element` 형태로 사용할 수 있다.
- `block2__element`에 여백이나 위치를 지정하고 block1은 독립적으로 유지할 수 있다.
예)
``` html
<div class="header">
  <div class="search-form header__search-form"></div>
</div>
```
- - -
처음엔 이러한 방법론이 너무 거추장스럽고 거부감이 들어 받아들이지 않았지만, 프로젝트의 규모가 커질수록 그리고 협업에서의 이러한 최소한의 규칙(일관성)은 필요하다고 생각합니다.

하지만, 위의 내용을 모두 그대로 사용하는 것이 아닌. 팀 또는 프로젝트 내에서 정비하여 대부분이 만족할 수 있는 더 나은 규칙을 만들어나가는 것이 중요할 것입니다.

## 참고 링크
- [https://medium.com/witinweb/css-%EB%B0%A9%EB%B2%95%EB%A1%A0-1-bem-block-element-modifier-1c03034e65a1](https://medium.com/witinweb/css-%EB%B0%A9%EB%B2%95%EB%A1%A0-1-bem-block-element-modifier-1c03034e65a1)
- [https://webclub.tistory.com/263](https://webclub.tistory.com/263)
- [https://a-tothe-z.tistory.com/2](https://a-tothe-z.tistory.com/2)