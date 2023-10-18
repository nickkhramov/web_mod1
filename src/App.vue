<template>
  <div id="app">
    <WindowApp/>
  </div>
</template>

<script>
import WindowApp from './components/WindowApp.vue'

export default {
  name: 'App',
  components: {
    WindowApp
  }
}
</script>

<style lang="scss">
  @import "./assets/styles/index.css";
</style>