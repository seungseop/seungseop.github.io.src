---
title: "[VSCode 확장] Vue Snippets"
categories: VSCode
tags:
- vscode
- extensions
- vue
- snippets
---
## Vue Snippets
뷰 컴포넌트 추가할때마다 SFC(Single File Components) 스타일(`<template>`, `<script>`, `<style>`)을 일일히 치는게 귀찮다보니 찾아봤다.

검색해보니 대표적으로 세개가 눈에 띄었다.
- Vetur
- Vue 2 Snippets
- Vue VSCode Snippets

전부 다뤄보고 싶지만, 일단 내가 사용하는 것 위주로 차근차근 업데이트 해보도록 한다.

### Vetur
> 아직 쓰는게 없다.

### Vue 2 Snippets
> 아직 쓰는게 없다.

### Vue VSCode Snippets
VSCode 확장(Extensions)에서 `Vue VSCode Snippets`설치.
{% asset_img image1.jpg %}

#### Usage
**Vue Base**
- vbase : 뷰(vue) 파일의 기본 형태를 구성해준다. (TypeScript는 `vbase-ts`를 사용)
``` html
<template>
  <div>

  </div>
</template>

<script>
  export default {

  }
</script>

<style lang="scss" scoped>

</style>
```

**&lt;Template&gt;**
- vfor
``` html
<div v-for="item in items" :key="item.id">
  {{ item }}
</div>
```