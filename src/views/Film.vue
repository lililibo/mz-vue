<template>
  <div>
    <Banner :banners="bannerList"></Banner>
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
      axios.get('https://m.maizuo.com/gateway?type=2&cityId=440300&k=5889141', {
        headers: {
          'X-Client-Info': '{"a":"3000","ch":"1002","v":"1.0.0","e":"15543712411546188226643"}',
          'X-Host': 'mall.cfg.common-banner'
        }
      }).then(res => {
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
