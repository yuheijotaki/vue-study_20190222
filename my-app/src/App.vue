<template>
  <div id="app">
    <header>
      <h1><router-link to="/">works.yuheijotaki.com</router-link></h1>
      <nav>
        <ul>
          <Navigation @event-one="onEventOne"></Navigation>
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
import Navigation from './components/navi.vue';

export default {
  name: 'App',
  data() {
    return {
      posts: []
    }
  },
  components: {
    Navigation
  },
  methods: {
    // onEventOne () {
    //   alert('event01');
    // },
    onEventOne: function(event) { // カテゴリーがクリックされたとき用のメソッド
      // 全体のナビゲーションのクラス削除
      var targetElements = document.getElementsByClassName('naviLink');
      // [].forEach.call(targetElements, function(elem) {
      //   elem.classList.remove('is-selected');
      // });
      // 選択したナビゲーションのクラス付与
      // event.currentTarget.classList.add('is-selected');
      // 投稿の取得
      const posts = this.posts;
      console.log(posts);
      // const selectedCategory = event.currentTarget.getAttribute('data-category'); // クリックしたカテゴリーの取得
      // if ( selectedCategory !== 'All' ) {
      //   // `All` 以外を選択した場合
      //   for (var i = 0; i < posts.length; i++) { // 投稿ごとのループ
      //     const categories = posts[i].category_name; // 投稿のカテゴリーを取得
      //     const categoriesArray = categories.split(' ,'); // 取得したカテゴリーを配列に変換
      //     for (var j = 0; j < categoriesArray.length; j++) { // 投稿内のカテゴリーごとのループ
      //       if ( categoriesArray.indexOf(selectedCategory) >= 0 ) { // 投稿に属するカテゴリーが含まれる場合
      //         posts[i].customData.display = true;
      //         break;
      //       } else { // マッチしない場合
      //         posts[i].customData.display = false;
      //       }
      //     }
      //   }
      // } else {
      //   // `All` を選択した場合
      //   for (var i = 0; i < posts.length; i++) { // 投稿ごとのループ
      //     posts[i].customData.display = true; // すべての投稿の `display` を `true` に
      //   }
      // }
    }
  }
}
</script>

<style lang="scss">
html,* {
  margin: 0;
  padding: 0;
}
h1,h2,h3,h4,h5,h6 {
  margin: 0;
  padding: 0;
}
#app {
  font-family: Helvetica Neue, Helvetica, Arial, 'Hiragino Kaku Gothic ProN', Meiryo, sans-serif;
  -webkit-text-size-adjust: 100%;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-rendering: optimizeLegibility;
  font-feature-settings : "palt";
  max-width: 800px;
  margin: 40px auto;
  letter-spacing: .01em;
  header {
    display: flex;
    align-items: flex-end;
    h1 {
      color: #222;
      font-size: 20px;
      line-height: 1.2;
      a {
        color: #222;
        text-decoration: none;
      }
    }
    nav {
      margin-left: auto;
      ul {
        display: flex;
        list-style: none;
        li {
          font-size: 13px;
          line-height: 1.2;
          margin-right: 20px;
          &:last-child {
            margin-right: 0;
          }
          a {
            color: #ccc;
            text-decoration: none;
            &.is-selected {
              color: #222;
            }
          }
        }
      }
    }
  }
  main {
    margin-top: 40px;
  }
}
</style>
