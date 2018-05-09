<template>
  <div class="warpper">
    <swiper :options="swiperOption">
      <!-- slides -->
      <swiper-slide v-for="item of imgLists" :key="item.id">
        <img :src="item.imgUrl" alt="" class="swiper-img">
      </swiper-slide>
      <!-- Optional controls -->
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeSwiper',
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true
      },
      imgLists: [{
        id: '0001',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1805/9e/f625886dec6c0402.jpg_750x200_417be630.jpg'
      }, {
        id: '0002',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1804/13/e1188b0d0f21b902.jpg_750x200_f85c782a.jpg'
      }, {
        id: '0003',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1609/f8/ef0b29100632f002.jpg_750x200_ebe20c8f.jpg'
      }]
    }
  }
}
</script>

<style lang="stylus" scoped>
  .warpper >>>  .swiper-pagination-bullet-active
    background #fff !important
  .warpper
    width 100%//也可以直接使用 height 26.6vw,视图宽度尺寸
    overflow hidden
    height 0
    padding-bottom 26.6%
    .swiper-img
      width 100%
</style>
