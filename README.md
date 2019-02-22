# Vue.js / JSON から情報を引っ張ってくる その7

## やること

- 前回のファイルを引き継いで Vue Router を使用して新しいページ（ `/about/` ）を作成する。

### ページごとにファイルを分ける

#### `/src/router/index.js`

```javascript
import Vue from 'vue'
import Router from 'vue-router'
import top from '@/components/top'
import about from '@/components/about'
Vue.use(Router)
export default new Router({
  routes: [
    {
      path: "/",
      name: 'top',
      component: top
    },
    {
      path: "/about",
      name: 'about',
      component: about
    }
  ]
})
```

#### `/src/App.vue`

```javascript
<template>
  <div id="app">
    <header>
      <h1><router-link to="/">works.yuheijotaki.com</router-link></h1>
      <nav>
        <ul>
          <li>
            <router-link to="/about">About</router-link>
          </li>
        </ul>
      </nav>
    </header>
    <main>
      <router-view></router-view>
    </main>
  </div>
</template>

<script>
// normalize.css を読み込む
import "normalize.css";
export default {
  name: 'App'
}
</script>
```

#### `/src/components/top.vue`

```javascript
<template>
  <!-- トップページの `<router-view>` にいれる内容 -->
  <p>トップページです。</p>
</template>

<script>
export default {
  name: 'top',
  data () {
    return {
      ...
    }
  },
  methods: {
    ...
  }
}
</script>
```

#### `/src/components/about.vue`

```javascript
<template>
  <!-- アバウトページの `<router-view>` にいれる内容 -->
  <p>アバウトページです。</p>
</template>

<script>
export default {
  name: 'about',
  data () {
    return {
      ...
    }
  },
  methods: {
    ...
  }
}
</script>
```

## まとめ

[**Github**](https://github.com/yuheijotaki/vue-study_20190222)

- `props` , `$emit` などを使ってコンポーネント間のデータの受け渡しを実装する