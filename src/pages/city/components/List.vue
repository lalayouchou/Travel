<template>
  <div>
    <div class="list" ref="wrapper">
      <div class="content">
        <div class="area">
          <div class="area-title border-topbottom">
            当前位置
          </div>
          <div class="area-botton">
            <div class="botton-wrapper">
              <div class="botton">北京</div>
            </div>
          </div>
        </div>
        <div class="area">
          <div class="area-title border-topbottom">
           热门城市
          </div>
          <div class="area-botton">
            <div class="botton-wrapper">
              <div class="botton">北京</div>
            </div>
            <div class="botton-wrapper">
              <div class="botton">北京</div>
            </div>
            <div class="botton-wrapper">
              <div class="botton">北京</div>
            </div>
            <div class="botton-wrapper">
              <div class="botton">北京</div>
            </div>
            <div class="botton-wrapper">
              <div class="botton">北京</div>
            </div>
            <div class="botton-wrapper">
              <div class="botton">北京</div>
            </div>
            <div class="botton-wrapper">
              <div class="botton">北京</div>
            </div>
            <div class="botton-wrapper">
              <div class="botton">北京</div>
            </div>
            <div class="botton-wrapper">
              <div class="botton">北京</div>
            </div>
          </div>
        </div>
        <div class="area">
          <div class="area-title border-bottom city-title">
           A
          </div>
          <div class="city-list">
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
          </div>
        </div>
        <div class="area">
          <div class="area-title border-bottom city-title">
           A
          </div>
          <div class="city-list">
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
          </div>
        </div>
        <div class="area">
          <div class="area-title border-bottom city-title">
           A
          </div>
          <div class="city-list">
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
            <div class="city border-bottom">阿克苏</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Bscoll from 'better-scroll'
export default {
  name: 'CityList',
  mounted () {
    this.scroll = new Bscoll(this.$refs.wrapper)
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/iconfont/variable.styl'
.border-topbottom
  &:before
    background #777
  &:after
    background #777
.border-bottom
  &:before
    background #777
.list
  position absolute
  left 0
  right 0
  top 1.64rem
  bottom 0
  overflow hidden
  .area
    .area-title
      line-height .6rem
      padding-left .3rem//不可以使用margin，这里有背景颜色和边框，会缺失一部分
      background #eaeaea
    .area-botton
      padding .1rem .7rem .1rem .2rem//也可使用margin
      overflow hidden
      .botton-wrapper
        float left
        width 33.3%
        .botton
          margin .1rem
          line-height .5rem
          text-align center
          border .02rem solid #777
          border-radius .04rem
    .city-title
      background transparent
    .city-list
      .city
        padding-left .3rem
        line-height .6rem
</style>
