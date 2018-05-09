<template>
  <div class="hander">
      <div class="hander-left">
        <div class="iconfont">&#xe624;</div>
      </div>
      <div class="hander-input">
        <span class="iconfont">&#xe632;</span>
        输入城市/景点/游玩主题</div>
      <div class="hander-right">
        城市
        <span class="iconfont arrow-icon">&#xe6aa;</span>
      </div>
  </div>
</template>

<script>
export default {
  name: 'HomeHeader'
}
</script>

<style lang="stylus" scoped>
@import '~styles/iconfont/variable.styl'
.hander
  display flex
  line-height .86rem
  background $bgColor
  color #fff
  .hander-left
    width .8rem
    text-align center
    span
      line-height .64rem
  .hander-input
    flex 1
    line-height .64rem
    height .64rem
    color #eeeeee
    margin-top .12rem
    margin-left .1rem
    background #ffffff
    border-radius .1rem
    text-indent .2rem//padding-left .2rem
  .hander-right
    width 1.14rem
    text-align center
    padding-left .2rem
    .arrow-icon
      font-size .36rem
      display inline-block
      transform translate(-.04rem,.04rem)//margin-left -.04rem
</style>
