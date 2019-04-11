<template>
  <div class="swiper-container billboards">
    <div class="swiper-wrapper">
      <div class="swiper-slide" v-for="(item, index) in banners" :key="index">
        <img :src="item.imgUrl" alt>
      </div>
    </div>
    <!-- 分页器 -->
    <div class="swiper-pagination"></div>
  </div>
</template>

<script>
import Swiper from 'swiper'
import 'swiper/dist/css/swiper.min.css'
export default {
  props: {
    banners: {
      type: Array
    }
  },
  data () {
    return {
      swiper: null
    }
  },
  updated () {
    if (!this.swiper) {
      this.swiper = new Swiper('.swiper-container', {
        loop: true,
        pagination: {
          el: '.swiper-pagination'
        }
      })
    }
  }
}
</script>

<style lang="less">
.swiper-container {
  width: 100%;
  height: 2.1rem;
  img {
    width: 100%;
  }
  .swiper-pagination-bullet {
    background: #fff;
    opacity: 1;
  }
  .swiper-pagination-bullet-active {
    background: red;
  }
  .swiper-pagination {
    position: absolute;
    width: 1.5rem;
    height: 0.07rem;
    bottom: .2rem;
    left: 2.2rem;
    .swiper-pagination-bullet {
      width: .05rem;
      height: .05rem;
      border-radius: 100%;
      margin-right: .03rem;
      background: rgba(255, 255, 255, 0);
      border: 1px solid white;
    }
    .swiper-pagination-bullet-active{
      background: #fff;
    }
  }
}
</style>
