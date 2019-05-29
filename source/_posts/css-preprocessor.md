---
title: CSS Preprocessor (Sass vs Less vs Stylus)
categories: CSS
tags:
  - CSS
  - StyleSheet
  - CSS Preprocessor
date: 2019-05-29 15:38:54
---

CSS는 매우 뛰어난 표준 스타일 언어 입니다. 하지만 표준화된 기술은 어떤 개인이나 특정 단체가 혼자서 그 기술을 확정하는 것이 아닌 표준화 위원회가 장기간에 걸친 논의를 통해 그 기술의 개선안을 발표하기 때문에 모든 면에서 좋을수는 없습니다.
그래서 어떤 이들은 CSS에 편리한 기능을 더한 새로운 언어를 만들고 이 언어에 따라서 작성한 코드를 어떤 프로그램으로 실행시키면 결과적으로 CSS를 만들어주는 도구들을 개발했는데요, 이런 도구를 전처리기(Preprocessor)라고 합니다. 이런 도구들의 개념을 알아봅니다.

## CSS Preprocessor
CSS Preprocessor 비교 사이트 : [https://csspre.com/compile/](https://csspre.com/compile/)

대표적인 CSS Preprocessor 세가지
- [Sass(SCSS)](https://sass-lang.com/)
  Sass는 Sass와 SCSS의 두가지 문법이 있습니다. 가장 오래된 CSS Preprocessor 언어이며 그만큼 높은 성숙도와 많은 커뮤니티를 보유하고 있습니다. 태생이 Ruby 기반이기 때문에 사용하는 것에 대해 제약이 있었으나 현재는 C++ 기반의 libsass, Node 기반의 node-sass가 추가되고 계속 업데이트 되면서 rubysass의 대부분의 기능이 그대로 구현되어 문제없이 사용 가능합니다.
- [Less](http://lesscss.org/)
  Node 기반으로 구동되어 자바스크립트 문법을 취하고 있습니다. 브라우저단에서도 동작하며, 비교적 쉽고 간단하게 작성이 가능해 진입장벽이 낮습니다. 다른 언어에 비해 기능적으로 일부 부족한 부분이 존재합니다.
- [Stylus](http://stylus-lang.com/)
  가장 뒤 늦게 나온 언어이며 그만큼 커뮤니티가 적습니다. Node 기반으로 구동되고 문법이 굉장히 유연하다(세련됐다)는 특징이 있습니다. 하지만 너무 관대한 문법이 독이 될 수 있어 CSS와 stylus 문법의 구분이 모호하기 때문에 초보자가 함부로 쓰기 위험할 수 있다는 단점도 존재합니다. 또한 문법의 성숙도가 가장 낮기때문에 작성하다보면 당황스러운 버그들을 만날 수도 있습니다.

### 참고 링크
  [[생활코딩] CSS 뛰어넘기(preprocessor)](https://opentutorials.org/course/2418/13468)