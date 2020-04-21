<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Article />
  </div>
</template>

<script>
import Article from './components/Article.vue'

export default {
  name: 'App',
  components: {
    Article
  }
}
</script>

<style lang="scss">
:root {
  --violet: #8865FF;
  --pink: #FF6FA5;
  --light-pink: #FB9EC4;
  --dirty-orange: #FFDAC0;
  --creme-orange: #FFC7BA;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
