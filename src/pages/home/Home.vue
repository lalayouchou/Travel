<template>
  <div>
    <home-header :city="city"></home-header>
    <home-swiper :list="swiperList"></home-swiper>
    <home-icons :list="iconList"></home-icons>
    <home-recommend :list="recommendList"></home-recommend>
    <home-weekend :list="weekendList"></home-weekend>
  </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper.vue'
import HomeIcons from './components/Icons.vue'
import HomeRecommend from './components/Recommend.vue'
import HomeWeekend from './components/Weekend.vue'
import axios from 'axios'
export default {
  name: 'Home',
  components: {
    HomeSwiper,
    HomeHeader,
    HomeIcons,
    HomeRecommend,
    HomeWeekend
  },
  mounted () {
    this.getHomeInfo()
  },
  data () {
    return {
      city: '',
      swiperList: [],
      iconList: [],
      recommendList: [],
      weekendList: []
    }
  },
  methods: {
    getHomeInfo () {
      axios.get('/api/index.json')
        .then(this.getHomeInfoSucc).catch(this.getHomeInfoFail)
    },
    getHomeInfoSucc (msg) {
      const message = msg.data
      if (message.ret && message.data) {
        this.city = message.data.city
        this.swiperList = message.data.swiperList
        this.iconList = message.data.iconList
        this.recommendList = message.data.recommendList
        this.weekendList = message.data.weekendList
      }
    },
    getHomeInfoFail (error) {
      console.log(error)
    }
  }
}
</script>

<style>

</style>
