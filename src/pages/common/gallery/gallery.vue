<template>
  <div>
    <div class="container" @click="handGalleryClick" ref="container">
      <div class="wrapper">
        <swiper :options="swiperOption">
          <swiper-slide v-for="(item,index) of imgs" :key="index">
            <img :src="item" class="gallery-img">
          </swiper-slide>
          <div class="swiper-pagination"  slot="pagination"></div>
        </swiper>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CommonGallery',
  props: {
    imgs: {
      type: Array,
      default: function () {
        return []
      }
    }
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
        observer: true,
        observeParents: true
      }
    }
  },
  methods: {
    handGalleryClick (e) {
      if (e.target === this.$refs.container) {
        this.$emit('close')
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
  .container >>> .swiper-container
    overflow visible
  .container
    z-index 99
    position fixed
    top 0
    right 0
    left 0
    bottom 0
    display flex
    align-items center
    background #000
    .wrapper
      width 100%
      height 0
      padding-bottom 73.75%
      background #fff
      .gallery-img
        width 100%
      .swiper-pagination
        color #fff
        bottom -1rem
</style>
