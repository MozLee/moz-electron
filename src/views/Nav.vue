<template>
  <div id="navbar">
    <el-menu
    :default-active="activeIndex"
    class="el-menu-demo"
    mode="horizontal"
    @select="handleSelect"
    background-color="#545c64"
    text-color="#fff"
    active-text-color="#ffd04b"
    :router="true">
      <el-menu-item index="/">基础音效</el-menu-item>
      <el-menu-item index="/about" disabled>喊麦音效</el-menu-item>
      <el-menu-item index="/specail" disabled>特殊</el-menu-item>
    </el-menu>
  </div>
</template>
<script>
export default {
  data () {
    return {
      activeIndex: '/'
    }
  },
  methods: {
    handleSelect (val) {
      // this.$router.push('/about')
    }
  }
}
</script>
