<template>
  <div class="show">
    <ul>
      <li
      v-for="film in filmList"
      :key="film.filmId">
        <router-link :to="{ name: 'detail',params: { id: film.filmId } }">
          <div class="show_img">
            <img :src="film.poster" alt>
          </div>
          <div class="detail">
            <div class>
              <span class="name">{{ film.name }}</span>
              <span class="item">{{ film.filmType.name }}</span>
            </div>
            <div class>
              <span class="label">观众评分</span>
              <span class="grade">{{ film.grade }}</span>
            </div>
            <div class>
              <span class="label">主演：{{ actorsFn(film.actors) }}</span>
            </div>
            <div class>
              <span class="label">{{ film.nation }} | {{ film.runtime }}分钟</span>
            </div>
          </div>
          <div class="buy">购票</div>
        </router-link>
      </li>
    </ul>
    <div class="load-more" @click="loadMore" v-if="pageNum < totalPage">加载更多...</div>
    <div class="load-more" v-else>别点了，没有了</div>
  </div>
</template>

<script>
import Axios from 'axios'
export default {
  data () {
    return {
      filmList: [],
      pageNum: 1,
      pageSize: 10,
      total: 10
    }
  },
  computed: {
    totalPage () {
      return Math.ceil(this.total / this.pageSize)
    }
  },
  methods: {
    getList () {
      Axios.get('https://m.maizuo.com/gateway', {
        params: {
          cityId: 440300,
          pageNum: this.pageNum,
          pageSize: this.pageSize,
          type: 1,
          k: 4966144
        },
        headers: {
          'X-Client-Info': '{"a":"3000","ch":"1002","v":"1.0.0","e":"15546520171868310774513"}',
          'X-Host': 'mall.film-ticket.film.list'
        }
      }).then(res => {
        let data = res.data
        if (data.status === 0) {
          this.total = data.data.total
          this.filmList.push(...data.data.films)
        } else {
          alert(data.msg)
        }
      })
    },
    loadMore () {
      this.pageNum++
      this.getList()
    },
    actorsFn (actors = []) {
      let temp = actors.map(item => {
        return item.name
      })
      return temp.join('、')
    }
  },
  created () {
    this.getList()
  }
}
</script>

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
.load-more {
    height: 36px;
    line-height: 36px;
    text-align: center;
  }
</style>
