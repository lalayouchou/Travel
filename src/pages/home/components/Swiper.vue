<template>
  <div class="warpper">
    <swiper :options="swiperOption" v-if="showSwiper" >
      <!-- slides -->
      <swiper-slide v-for="item of list" :key="item.id">
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
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true,
        autoplay: 5000,
        autoplayDisableOnInteraction: false
      }
    }
  },
  computed: {
    showSwiper () {
      return this.list.length
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
    padding-bottom 31.25%
    .swiper-img
      width 100%
</style>
