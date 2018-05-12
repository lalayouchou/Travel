<template>
  <div class="hander">
      <div class="hander-left">
        <div class="iconfont">&#xe624;</div>
      </div>
      <div class="hander-input">
        <span class="iconfont">&#xe632;</span>
        输入城市/景点/游玩主题</div>
      <router-link to="/city">
        <div class="hander-right">
          {{this.city}}
          <span class="iconfont arrow-icon">&#xe6aa;</span>
        </div>
    </router-link>
  </div>
</template>

<script>
import { mapState } from 'vuex'
export default {
  name: 'HomeHeader',
  computed: {
    ...mapState(['city'])
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/iconfont/variable.styl'
@import '~styles/ellipsis.styl'
.hander
  display flex
  line-height .86rem
  background $bgColor
  color #fff
  .hander-left
    width .8rem
    text-align center
    font-weight bold
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
    text-indent .15rem//padding-left .2rem
    ellipsis()
  .hander-right
    min-width 1rem
    padding 0 .1rem 0 .2rem
    text-align center
    color #fff
    ellipsis()
    .arrow-icon
      font-size .36rem
      display inline-block
      transform translate(-.04rem,.04rem)//margin-left -.04rem
</style>
