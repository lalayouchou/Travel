<template>
  <div class="wrapper">
    <div class="banner" @click="handleBannerClick">
      <div class="header-back" @click.stop="HandleHeaderBack" v-show="showAbs">
        <div class="iconfont">&#xe624;</div>
      </div>
      <img :src="bannerImg">
      <div class="banner-info">
        <div class="banner-title">{{sightName}}}</div>
        <div class="banner-number">
          <span class="iconfont banner-icon">&#xe632;</span>6</div>
      </div>
      <div class="header-title" v-show="!showAbs" :style="opacityStyle">景点详情</div>
    </div>
    <common-gallery :imgs="gallery" v-show="showGallery" @close="closeGallery"></common-gallery>
  </div>
</template>

<script>
import CommonGallery from 'common/gallery/gallery.vue'
export default {
  name: 'DetailBanner',
  components: {
    CommonGallery
  },
  props: {
    bannerImg: String,
    sightName: String,
    gallery: Array
  },
  data () {
    return {
      showGallery: false,
      showAbs: true,
      imgs: ['http://img1.qunarzz.com/sight/p0/201408/14/d6a9132a38b185cd25e6c7c5d65e0454.jpg_r_800x800_34ac98c3.jpg',
        'http://img1.qunarzz.com/sight/p0/201408/14/dba7220ac844600c07a1af703f640935.jpg_r_800x800_7c25ace3.jpg'
      ],
      opacityStyle: {
        opacity: 0
      }
    }
  },
  activated () {
    window.addEventListener('scroll', this.handleScroll)
    console.log(top)
  },
  deactivated () {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    handleBannerClick () {
      this.showGallery = true
    },
    closeGallery () {
      this.showGallery = false
    },
    HandleHeaderBack () {
      this.$router.push('/')
    },
    handleScroll () {
      const top = document.documentElement.scrollTop
      if (top > 60) {
        let opacity = top / 140
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle = {
          opacity
        }
        this.showAbs = false
      } else {
        this.showAbs = true
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/iconfont/variable.styl'
.wrapper
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
    .header-back
      position absolute
      left .3rem
      top .3rem
      line-height .8rem
      height .8rem
      width .8rem
      background rgba(0,0,0,.6)
      color #fff
      border-radius 50%
      font-weight bold
      text-align center
    .header-title
      z-index 2
      position fixed
      top 0
      left 0
      right 0
      height $HeaderHeight
      line-height $HeaderHeight
      color #fff
      font-size .32rem
      text-align center
      background $bgColor
</style>
