<template>
  <div class="film-list">
    <Banner :banners="bannerList"></Banner>
    <div class="top">
      <router-link to="/films/nowPlaying" active-class="top_c">正在热映</router-link>
      <router-link to="/films/comingSoon" active-class="top_c">即将上映</router-link>
    </div>
    <router-view></router-view>
  </div>
</template>

<script>
import Banner from '../components/Banner'
import axios from 'axios'
export default {
  data () {
    return {
      bannerList: []
    }
  },
  components: {
    Banner
  },
  methods: {
    getBannerList () {
      /**
       * 请求轮播图的数据
       */
      axios
        .get('https://m.maizuo.com/gateway?type=2&cityId=440300&k=5889141', {
          headers: {
            'X-Client-Info':
              '{"a":"3000","ch":"1002","v":"1.0.0","e":"15543712411546188226643"}',
            'X-Host': 'mall.cfg.common-banner'
          }
        })
        .then(res => {
          let data = res.data
          if (data.status === 0) {
            this.bannerList = data.data
          } else {
            alert(data.msg)
          }
        })
    }
  },
  created () {
    this.getBannerList()
  }
}
</script>

<style>
@import "../styles/common/reset.css";
.film-list {
  padding-bottom: 50px;
}
.top {
  height: 0.49rem;
  display: flex;
  border-bottom: 1px solid #f6f6f6;
  line-height: 0.49rem;
  justify-content: space-around;
}
.top a {
  color: #191a1b;
  font-size: 0.16rem;
}
.top_c {
  display: block;
  border-bottom: 1px solid #ff5f16;
  color: #ff5f16 !important;
}
</style>
