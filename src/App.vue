<template>
  <div id="app">
    <MyHeader/>
    <Albums/>
  </div>
</template>

<script>

import MyHeader from './components/MyHeader.vue'
import Albums from './components/Albums.vue'

export default {
  name: 'App',
  components: {
    MyHeader,
    Albums
  }
}
</script>

<style lang="scss">
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  } 
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #807062;
}
</style>
