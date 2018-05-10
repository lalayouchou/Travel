<template>
  <div class="icons">
    <swiper :options="swiperOption">
      <swiper-slide v-for="(page,index) of pages" :key="index">
       <div class="icon" v-for="item of page" :key="item.id">
        <div class="icon-img">
          <img class="icon-img-content" :src="item.imgUrl" alt="">
        </div>
         <p class="icon-text">{{item.desc}}</p>
       </div>
      </swiper-slide>

   </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeIcons',
  props :{
    list: Array
  },
  data () {
    return {
      swiperOption: {
        loop: true,
        autopaly: false
      }
    }
  },
  computed: {
    pages () {
      let pages = []
      this.list.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/ellipsis.styl'
  .icons >>> .swiper-slide-active
    padding-bottom 50%
    height 0
  .icons
    margin-top .1rem
    .icon
      position relative
      width 25%
      padding-bottom 25%
      float left
      .icon-img
        position absolute
        left 0
        right 0
        top 0
        bottom .44rem
        .icon-img-content
          display block
          height 100%
          margin auto
          box-sizing border-box
          padding-top .1rem
      .icon-text
        position absolute
        bottom 0
        left 0
        right 0
        height .44rem
        line-height .44rem
        text-align center
        ellipsis()
</style>
