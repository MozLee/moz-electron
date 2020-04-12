<template>
  <div id="app">
    <Nav></Nav>
    <router-view></router-view>
  </div>
</template>

<script>
import Nav from './views/Nav'
export default {
  name: 'app',
  components: {
    Nav
  }
}
</script>

<style lang="scss">
@import "@/assets/css/reset.scss";
</style>
