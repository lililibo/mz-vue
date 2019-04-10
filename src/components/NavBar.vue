<template>
  <!--底部-->
  <div id="footer">
    <ul>
      <li v-for="(tab,index) in tabs"
      :key="index"
      >
        <router-link :to="tab.href"
        active-class="footer_c">
          <span :class="['iconfont', tab.icon]"></span>
          {{ tab.name }}
        </router-link>
      </li>
      <!-- <li>
        <a href="#">
          <span class="iconfont icon-yingyuana"></span>影院
        </a>
      </li>
      <li>
        <a href="#">
          <span class="iconfont icon-youhui"></span>特惠
        </a>
      </li>
      <li>
        <a href="#">
          <span class="iconfont icon-profile"></span>我的
        </a>
      </li> -->
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    tabs: {
      type: Array
    }
  }
}
</script>

<style>
@import "../styles/common/reset.css";
/*底部*/
#footer {
  position: fixed;
  width: 100%;
  bottom: 0;
  left: 0;
  box-sizing: border-box;
  background: #ffffff;
}
#footer ul{
  width: 100%;
  height: 0.49rem;
  box-sizing: border-box;
  display: flex;
  justify-content: space-around;
  align-items: center;
  background: #ffffff;
}
#footer a {
  display: flex;
  flex-direction: column;
  align-items: center;
  color: #797d82;
  font-size: 0.13rem;
}
.footer_c {
  color: #ff5f16 !important;
}
</style>
