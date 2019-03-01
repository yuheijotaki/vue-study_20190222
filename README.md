# Vue.js / JSON から情報を引っ張ってくる その8

## やること

- Vue Router を使用してコンポーネント間のメソッドの受け渡しする。

#### ファイル構成

`myButton.vue` で仕込んだクリックイベントを `App.vue` へ渡す。

```
.
├── index.js
├── App.vue
├── router
|   └── index.js
├── components
|   └── page
|				├── top.vue
|				└── about.vue
|   └── common
|				├── myHeader.vue
|				└── myFooter.vue
|   └── element
|				└── button
|						└── myButton.vue
```

#### `index.js`

受け渡しとはあまり関係ないですが、Vue Router を使う

```javascript
import Vue from 'vue'
import Router from 'vue-router'
import top from '@/components/page/top'
import about from '@/components/page/about'
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

#### `App.vue`

`myButton.vue` で仕込んだ　`'event-test'`  のメソッドを `myButton` のクリックイベントとして登録

```javascript
<template>
  <div id="app">
    <myHeader></myHeader>
    <main>
      <router-view></router-view>
      <myButton @event-test="clickAlert"></myButton>
    </main>
    <myFooter></myFooter>
  </div>
</template>

<script>
import "normalize.css";
import myHeader from './components/common/myHeader.vue';
import myFooter from './components/common/myFooter.vue';
import myButton from './components/element/button/myButton.vue';

export default {
  name: 'App',
  components: {
    myHeader,
    myFooter,
    myButton
  },
  methods: {
    clickAlert: function(event) {
      alert('event test');
    }
  }
}
</script>
```

#### `myButton.vue`

`'event-test'` を `$emit` しておく

```javascript
<template>
  <button @click="emitEventTest">Button</button>
</template>

<script>
export default {
  name: 'myButton',
  methods: {
    emitEventTest () {
      this.$emit('event-test',event)
    }
  }
}
</script>
```

## まとめ

[**Github**](https://github.com/yuheijotaki/vue-study_20190222)

- やること簡単にしようと思ってたらJSONは関係のない内容になってしまった。（前回の引き継いだ結果、ちょっと複雑になりすぎたので、簡単なコンテンツ内容にして進めるようにしました。）
- 次回はこれをベースにポートフォリオのサイトを作るの目標にします。ふつうのWebサイトなら Vue.js 使って構築できそうな気がしてきました。
- コンポーネントについては、[Vue\.jsコンポーネント入門 \| Hypertext Candy](https://www.hypertextcandy.com/vuejs-components-introduction-environment-setting) がわかりやすそうです。

**ほか参考にした記事など**

- [3連休だしVue\.jsをはじめよう：コンポーネントを使ってみる \- 豆腐とコンソメ](https://www.tohuandkonsome.site/entry/2017/10/09/004525)

- [vue\.js でコンポーネント間でデータ受け渡しとイベント発行周り \- Qiita](https://qiita.com/sasarkyz/items/347bcedec8e20d4fdd76)
- [【Vue\.jsでSPAへの移行】コンポーネントを使ってみよう \| orizuru](https://orizuru.io/blog/vue-js/component/)
