<template>
    <swiper :options="swiperOption">
    <!-- slides -->
    <swiper-slide>
      <img src="http://img1.qunarzz.com/piao/fusion/1805/9e/f625886dec6c0402.jpg_750x200_417be630.jpg" alt="" class="swiper-img">
    </swiper-slide>
    <swiper-slide><img src="http://img1.qunarzz.com/piao/fusion/1804/13/e1188b0d0f21b902.jpg_750x200_f85c782a.jpg" alt="" class="swiper-img">
    </swiper-slide>
    <swiper-slide><img src="http://img1.qunarzz.com/piao/fusion/1609/f8/ef0b29100632f002.jpg_750x200_ebe20c8f.jpg" alt="" class="swiper-img">
    </swiper-slide>
    <!-- Optional controls -->
    <div class="swiper-pagination"  slot="pagination"></div>
  </swiper>
</template>

<script>
export default {
  name: 'HomeSwiper',
  data () {
    return {
      swiperOption: {}
    }
  }
}
</script>

<style lang="stylus" scoped>
  .swiper-img
    width 100%
</style>
