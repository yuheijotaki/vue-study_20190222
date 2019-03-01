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
  max-width: 400px;
  margin: 40px auto;
  letter-spacing: .01em;
  main {
    margin-top: 40px;
    font-size: 13px;
    line-height: 1.6;
  }
}
</style>
