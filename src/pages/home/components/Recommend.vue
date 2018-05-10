<template>
  <div>
    <div class="recommend-title">
      热门推荐
    </div>
    <ul>
      <li class="item border-bottom" v-for="item of list" :key="item.id">
        <div class="item-img-wrapper">
          <img :src="item.imgUrl" alt="" class="item-img">
        </div>
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
          <button class="item-button">查看详情</button>
        </div>
      </li>
    </ul>
    <div class="recommend-more">
      <a>查看更多相关推荐</a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/ellipsis.styl'
  .recommend-title
    margin-top .2rem
    line-height .6rem
    background #eee
    text-indent .2rem
  .item
    display flex
    height 1.9rem
    .item-img-wrapper
      width 1.5rem
      height 1.5rem
      padding .2rem
      .item-img
        width 100%
    .item-info
      flex 1
      padding .2rem
      min-width 0
      .item-title
        line-height .44rem
        font-size .32rem
        ellipsis()
      .item-desc
        height .6rem
        line-height .6rem
        color #aaa
        ellipsis()
      .item-button
        background #ff9300
        border-radius .05rem
        font-size .2rem
        padding .05rem .2rem
        line-height .3rem
        margin-top .05rem
        color #fff
        font-weight bold
  .recommend-more
    a
      display block
      line-height .8rem
      text-align center
</style>
