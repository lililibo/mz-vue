<template>
  <div class="show">
    <ul>
      <li>
        <a href="#">
          <div class="show_img">
            <img src="https://static.maizuo.com/v5/upload/69d58c31feb894f3142461b7357ef81c.jpg?x-oss-process=image/quality,Q_70">
          </div>
          <div class="detail">
            <div class>
              <span class="name">波西米亚狂想曲</span>
              <span class="item">2D</span>
            </div>
            <div class>
              <span class="label">观众评分</span>
              <span class="grade">8.6</span>
            </div>
            <div class>
              <span class="label">主演：布莱恩·辛格 约瑟夫·梅泽罗 拉米·马雷克 本·哈迪</span>
            </div>
            <div class>
              <span class="label">英国 美国 | 135分钟</span>
            </div>
          </div>
          <div class="buy">预购</div>
        </a>
      </li>
    </ul>
  </div>
</template>

<style>
.show ul li a {
  display: flex;
  justify-content: space-between;
  height: 1.24rem;
  padding: 0.15rem;
  box-sizing: border-box;
}
.show_img {
  width: 0.66rem;
  height: 0.94rem;
}
.show_img img {
  width: 100%;
  height: 100%;
}
.detail {
  width: 2.29rem;
  height: 0.81rem;
  box-sizing: border-box;
  margin: 0.05rem 0.1rem;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
.name {
  color: #191a1b;
  font-size: 0.16rem;
  height: 0.22rem;
  line-height: 0.22rem;
  margin-right: 0.05rem;
  overflow: hidden;
}
.item {
  font-size: 0.09rem;
  color: #fff;
  background-color: #d2d6dc;
  height: 0.14rem;
  line-height: 0.14rem;
  padding: 0 0.02rem;
  border-radius: 0.02rem;
}
.label {
  font-size: 0.13rem;
  margin-top: 0.04rem;
  color: #797d82;
}
.grade {
  color: #ffb232;
  font-size: 0.14rem;
}
.buy {
  line-height: 0.25rem;
  border: 1px solid #ff5f16;
  margin-top: 0.25rem;
  height: 0.25rem;
  width: 0.5rem;
  color: #ff5f16;
  font-size: 0.13rem;
  text-align: center;
  border-radius: 0.02rem;
}
</style>
