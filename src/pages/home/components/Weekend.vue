<template>
  <div>
    <div class="recommend-title">
      周末去哪儿
    </div>
    <ul>
      <li class="item border-bottom" v-for="item of list" :key="item.id">
        <div class="item-img-wrapper">
          <img :src="item.imgUrl" alt="" class="item-img">
        </div>
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeWeekend',
  props :{
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/ellipsis.styl'
  .recommend-title
    line-height .8rem
    background #eee
    text-indent .2rem
  .item
    .item-img-wrapper
      height 0
      padding-bottom 37%
      overflow hidden
      .item-img
        width 100%
    .item-info
      padding .2rem
      border-bottom .1rem solid rgb(235,235,235)
      .item-title
        line-height .4rem
        font-size .28rem
        ellipsis()
      .item-desc
        height .5rem
        line-height .5rem
        font-size .24rem
        color #aaa
        ellipsis()
</style>
