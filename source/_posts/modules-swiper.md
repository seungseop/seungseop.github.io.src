---
title: Swiper.js (with. Vue.js)
categories: Modules
tags:
  - npm
  - modules
  - swiper
  - slider
  - carousel
date: 2019-05-21 16:37:15
---

## [Swiper.js](http://idangero.us/swiper/)
꽤 괜찮은 javscript Slider(Carousel) 라이브러리인 `Swiper.js`를 사용해보자.
-  DOCS : [http://idangero.us/swiper/api/](http://idangero.us/swiper/api/)

### [Vue (vue-awesome-swiper)](https://github.com/surmon-china/vue-awesome-swiper)
Swiper.js의 Vue.js 호환 버전이다. [DEMO > ](https://surmon-china.github.io/vue-awesome-swiper/)

#### 설치하기(Installation)
``` bash
# npm
$ npm install vue-awesome-swiper --save
# yarn
$ yarn add vue-awesome-swiper --save
```

#### 사용하기(Mount)
**글로벌(global)**
``` js
import Vue from 'vue'
import VueAwesomeSwiper from 'vue-awesome-swiper'

// require styles
import 'swiper/dist/css/swiper.css'

Vue.use(VueAwesomeSwiper, /* { default global options } */)
```

`Nuxt.js`에서 글로벌로 사용할 때, `plugins/`폴더 내에 다음과 같이 사용한다.
``` js
// plugins/swiper.js

import Vue from 'vue'
import VueAwesomeSwiper from 'vue-awesome-swiper/dist/ssr'

// require styles
import 'swiper/dist/css/swiper.css'

Vue.use(VueAwesomeSwiper, /* { default global options } */)
```
`nuxt.config.js`내의 `plugins`속성 값 추가
``` js
module.exports = {
  ...
  /*
  ** Plugins to load before mounting the App
  */
  plugins: [
    { src: '~/plugins/swiper.js', ssr: false },
  ]
  ...
}
```

**컴포넌트(component)**
``` js
// require styles
import 'swiper/dist/css/swiper.css'

import { swiper, swiperSlide } from 'vue-awesome-swiper'

export default {
  components: {
    swiper,
    swiperSlide
  }
}
```

**SSR 환경**
``` js
// 만약 Nuxt.js(SSR) 환경이라면, 브라우저 환경(process.browser)에서만 사용
if (process.browser) {
  const VueAwesomeSwiper = require('vue-awesome-swiper/dist/ssr')
  Vue.use(VueAwesomeSwiper)
}
```

**Swiper 플러그인 옵션 변경**
``` js
import Swiper from 'swiper'
Swiper.use({
  name: 'pluginName',
  params: {
    pluginSwitch: false,
  },
  on: {
    init() {
      if (!this.params.pluginSwitch) return
      console.log('init')
    },
    // swiper callback...
  }
})
```

#### 차이점(Difference)
`SSR`과 `SPA`에서 사용할 때 유일한 차이점 :
- `SPA`는 컴포넌트(`component`) 형태로 사용하고, `ref` 속성으로 `Swiper`인스턴스를 찾으세요.
- `SSR`은 디렉티브(`directive`) 형태로 사용하고, `directive arg`로 `Swiper`인스턴스를 찾으세요.
- 다른 환경과 이벤트는 동일합니다.

**SPA**
``` html
<!-- The ref attr used to find the swiper instance -->
<template>
  <swiper :options="swiperOption" ref="mySwiper" @someSwiperEvent="callback">
    <!-- slides -->
    <swiper-slide>I'm Slide 1</swiper-slide>
    <swiper-slide>I'm Slide 2</swiper-slide>
    <swiper-slide>I'm Slide 3</swiper-slide>
    <swiper-slide>I'm Slide 4</swiper-slide>
    <swiper-slide>I'm Slide 5</swiper-slide>
    <swiper-slide>I'm Slide 6</swiper-slide>
    <swiper-slide>I'm Slide 7</swiper-slide>
    <!-- Optional controls -->
    <div class="swiper-pagination"  slot="pagination"></div>
    <div class="swiper-button-prev" slot="button-prev"></div>
    <div class="swiper-button-next" slot="button-next"></div>
    <div class="swiper-scrollbar"   slot="scrollbar"></div>
  </swiper>
</template>

<script>
  export default {
    name: 'carrousel',
    data() {
      return {
        swiperOption: {
          // swiper 옵션, 콜백함수 모두 동일하게 사용
        }
      }
    },
    computed: {
      swiper() {
        return this.$refs.mySwiper.swiper
      }
    },
    mounted() {
      // 현재 swiper 인스턴스를 확인
      console.log('this is current swiper instance object', this.swiper)
      this.swiper.slideTo(3, 1000, false)
    }
  }
</script>
```

**비동기 데이터에서의 사용 예제**
``` html
<template>
  <swiper :options="swiperOption">
    <swiper-slide v-for="(slide, index) in swiperSlides" :key="index">I'm Slide {{ slide }}</swiper-slide>
    <div class="swiper-pagination" slot="pagination"></div>
  </swiper>
</template>

<script>
  export default {
    name: 'carrousel',
    data() {
      return {
        swiperOption: {
          pagination: {
            el: '.swiper-pagination'
          }
        },
        swiperSlides: [1, 2, 3, 4, 5]
      }
    },
    mounted() {
      setInterval(() => {
        console.log('simulate async data')
        if (this.swiperSlides.length < 10) {
          this.swiperSlides.push(this.swiperSlides.length + 1)
        }
      }, 3000)
    }
  }
</script>
```

**SSR**
``` html
<!-- You can custom the "mySwiper" name used to find the swiper instance in current component -->
<template>
  <div v-swiper:mySwiper="swiperOption" @someSwiperEvent="callback">
    <div class="swiper-wrapper">
      <div class="swiper-slide" v-for="banner in banners">
        <img :src="banner">
      </div>
    </div>
    <div class="swiper-pagination"></div>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        banners: [ '/1.jpg', '/2.jpg', '/3.jpg' ],
        swiperOption: {
          pagination: {
            el: '.swiper-pagination'
          },
          // some swiper options...
        }
      }
    },
    mounted() {
      setTimeout(() => {
        this.banners.push('/4.jpg')
        console.log('banners update')
      }, 3000)
      console.log(
        'This is current swiper instance object', this.mySwiper, 
        'It will slideTo banners 3')
      this.mySwiper.slideTo(3, 1000, false)
    }
  }
</script>
```