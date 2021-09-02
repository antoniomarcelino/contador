<template>
  <div id="app">
      <Home />
  </div>
</template>

<script>
import Home from './views/Home.vue'

export default {
  components: { Home },
  name: 'App'
}
</script>

<style>
* {
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
}

#app {
  font-family: 'Red Hat Text', sans-serif;
  font-weight: bold;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ffffff;
  background: url("./assets/pattern-hills.svg") repeat-x 0 bottom, url("./assets/bg-stars.svg"), #1b1924;
  height: 100vh;
  margin: 0;
}
</style>
