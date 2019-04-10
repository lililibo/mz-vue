<template>
  <div id="app">
    <router-view></router-view>
    <NavBar :tabs="tabs"></NavBar>
  </div>
</template>

<script>
import NavBar from './components/NavBar'
export default {
  name: 'app',
  data () {
    return {
      tabs: [
        { name: '电影', href: '/films', icon: 'icon-dianying' },
        { name: '影院', href: '/cinemas', icon: 'icon-yingyuana' },
        { name: '特惠', href: '/sales', icon: 'icon-youhui' },
        { name: '我的', href: '/center', icon: 'icon-profile' }
      ]
    }
  },
  components: {
    NavBar
  }
}
</script>

<style>
@import "./styles/base.css";
</style>
