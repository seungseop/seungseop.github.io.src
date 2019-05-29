---
title: Sass(SCSS)
categories: Sass
tags:
  - Sass
  - CSS
  - CSS Preprocessor
date: 2019-05-29 15:40:48
---

CSS Preprocessor 중 하나인 Sass(SCSS)를 간단히 살펴보고 컴파일하는 방법을 알아봅니다.

## Sass(SCSS)
<img src="/images/sass.png" width="300" style="border:0 none;" />
> Sass는 기초 언어에 힘과 우아함을 더해주는 CSS의 확장이다.

### Sass와 SCSS의 차이점
SCSS는 CSS 구문과 완전히 호환되도록 새로운 구문을 도입해 만든 Sass의 모든 기능을 지원하는 CSS의 상위집합(Superset) 입니다.
간단한 차이는 `{}`(중괄호)와 `;`(세미콜론)의 유무입니다.

- **Sass**
``` sass
.list
  width: 100px
  float: left
  li
    color: red
    background: url("./image.jpg")
    &:last-child
      margin-right: -10px
```

- **SCSS**
``` scss
.list {
  width: 100px;
  float: left;
  li {
    color: red;
    background: url("./image.jpg");
    &:last-child {
      margin-right: -10px
    }
  }
}
```
Sass는 선택자의 유효범위를 `‘들여쓰기’`로 구분하고, SCSS는 `{}`로 범위를 구분합니다.

또한 Mixins(믹스인, 재사용 가능한 기능을 만드는 방식) 사용에도 차이가 있습니다.
(Sass는 단축 구문으로 사용합니다.)
- **Sass**
``` sass
=border-radius($radius)
  -webkit-border-radius: $radius
  -moz-border-radius:    $radius
  -ms-border-radius:     $radius
  border-radius:         $radius

.box
  +border-radius(10px)
```

- **SCSS**
``` scss
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
     -moz-border-radius: $radius;
      -ms-border-radius: $radius;
          border-radius: $radius;
}

.box { @include border-radius(10px); }
```
**Sass**는 `=`와 `+` 기호로 Mixins 기능을 사용했고, **SCSS**는 `@mixin`과 `@include`로 기능을 사용했습니다.

거의 차이가 없지만 복잡한 문장이 될 경우 장단점이 있을 수 있습니다.
**Sass는 좀 더 간결하고 작성하기 편리**하며, `{}`나 `;`를 사용하지 않아도 되니 **코드가 훨씬 깔끔해집니다.**
**SCSS는 인라인 코드(한 줄 작성)를 작성**할 수 있고, CSS와 유사한 문법을 가지기 때문에 **코드 통합이 훨씬 쉽습니다.**

보통의 경우 **SCSS**를 추천합니다.

### 컴파일 방법
Sass(SCSS)는 웹에서 직접 동작할 수 없습니다.
어디까지나 최종에는 표준 CSS로 동작해야 하며, 전처리기로 작성 후 CSS로 컴파일해야 합니다.
실무에서 활용하는 컴파일 방법들을 소개합니다.

#### SassMeister
간단한 Sass 코드는 [SassMeister](https://www.sassmeister.com/)를 사용해서 웹에서 바로 컴파일하여 사용할 수 있습니다.
페이지 접속 후 바로 Sass나 SCSS 문법으로 코딩하면 CSS로 실시간 변환 됩니다.
{% asset_img sassmeister.jpg %}

#### VSCode
VSCode에서는 Sass와 같은 Preprocessor 파일을 저장만하면 자동으로 컴파일 시켜주는 확장을 제공한다.
{% asset_img demo.gif %}

- [Easy Compile](https://github.com/refgd/easy-complie)
Sass / SCSS / Less / TYPESCRIPT 통합 easy compile
**설치**
{% asset_img easy_compile.jpg %}
**세팅**
``` js
// VSCode setting.json
{
	...
	"easycompile.sass" : {
			...
      "compress": true,
      "sourceMap": true,
      "autoprefixer": "> 1%, Last 3 versions, iOS 8", // IE9 이상
  },
  "easycompile.compile": {
      "ignore" : [
          "**/_*.*"
      ]
  },
}
```
easycompile.compile: 전체 언어에 해당하는 컴파일 옵션을 설정할 수 있다.(`ignore`옵션은 해당하는 파일은 컴파일하지 않는 파일. 예로 import에만 활용하는 파일)
easycompile.sass: Sass 언어에 해당하는 컴파일 옵션을 설정 할 수 있다.(compress, sourceMap, autoprefixer 등)

- [Easy Sass](https://github.com/wojciechsura/easysass)
위의 Easy Compile과 비슷하나 Sass만 지원하는 도구(Less의 컴파일을 지원하는 Easy Less도 존재)
**설치**
{% asset_img easy_sass.jpg %}
**세팅**
``` js
// VSCode setting.json
{
	...
	"easysass.excludeRegex": "^(_)[a-z]+.",
}
```
easysass.excludeRegex: 해당 정규식에 해당하는 파일은 컴파일하지 않는다.

#### node-sass
node-sass는 Node.js 컴파일러인 LibSass에 바인딩한 라이브러리 입니다.
NPM으로 전역 설치하여 사용해봅니다.

``` bash
$ npm install -g node-sass
```
컴파일하려는 파일의 경로와 컴파일된 파일이 저장될 경로를 설정합니다.
``` bash
# $ node-sass [옵션] <입력파일경로> <출력파일경로>
$ node-sass scss/main.scss public/main.css
```
여러 출력 경로를 설정할 수 있습니다.
``` bash
$ node-sass scss/main.scss public/main.css dist/style.css
```
옵션을 적용할 수도 있습니다.
옵션으로 `--watch`혹은 `-w`를 입력하면, 런타임 중 파일을 감시하여 저장 시 자동으로 변경 사항을 컴파일합니다.
``` bash
$ node-sass --watch scss/main.scss public/main.css
```
기타 옵션은 [node-sass CLI](https://github.com/sass/node-sass#command-line-interface)에서 확인할 수 있습니다.

## 참고 링크
- [Sass(SCSS) 완전 정복!](https://heropy.blog/2018/01/31/sass/)