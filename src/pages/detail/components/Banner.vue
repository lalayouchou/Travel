<template>
  <div>
    <div class="banner" @click="handleBannerClick">
      <img src="//img1.qunarzz.com/sight/p0/201406/24/e2a5766e6e81793b2b518a7a08812a4a.jpg_600x330_3a459e19.jpg" alt="" class="banner-img">
      <div class="banner-info">
        <div class="banner-title">千岛湖森林氧吧</div>
        <div class="banner-number">
          <span class="iconfont banner-icon">&#xe632;</span>6</div>
      </div>
    </div>
    <common-gallery :imgs="imgs" v-show="showGallery" @close="closeGallery"></common-gallery> 
  </div>
</template>

<script>
import CommonGallery from 'common/gallery/gallery.vue'
export default {
  name: "DetailBanner",
  components: {
    CommonGallery
  },
  data(){
    return {
      showGallery: false,
      imgs: ["http://img1.qunarzz.com/sight/p0/201408/14/d6a9132a38b185cd25e6c7c5d65e0454.jpg_r_800x800_34ac98c3.jpg",
        "http://img1.qunarzz.com/sight/p0/201408/14/dba7220ac844600c07a1af703f640935.jpg_r_800x800_7c25ace3.jpg"
      ]
    }
  },
  methods: {
    handleBannerClick () {
      this.showGallery = true
    },
    closeGallery () {
      this.showGallery = false
    }
  }
}
</script>

<style lang="stylus" scoped>
  .banner
    overflow hidden
    height 0
    padding-bottom 55%
    position relative
    .banner-img
      width 100%
    .banner-info
      position absolute
      left 0
      right 0
      bottom 0
      line-height .6rem
      color #fff
      display flex
      background-image: linear-gradient(top ,rgba(0,0,0,0),rgba(0,0,0,.8))
      .banner-title
        font-size .3rem
        flex 1
        padding 0 .2rem
      .banner-number
        height .4rem
        line-height .4rem
        min-width 1rem
        padding 0 .2rem
        margin-top .1rem
        font-size .3rem
        border-radius .2rem
        text-align center
        background rgba(0,0,0,.4)
        .banner-icon
          font-size .3rem
        
</style>