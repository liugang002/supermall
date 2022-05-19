<template>
  <div id="app">
    <router-view></router-view>
    <main-tab-bar-vue id='tab-bar'/>
  </div>
</template>

<script>
import MainTabBarVue from "components/content/mainTarbBar/MainTabBar.vue"
export default {
  name: 'App',
  components: {
    MainTabBarVue
  }
}
</script>

<style scoped>
@import url("assets/css/base.css");

</style>
