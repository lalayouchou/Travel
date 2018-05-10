<template>
  <div>
    <div class="header">
      <router-link to="/">
        <div class="iconfont header-back">&#xe624;</div>
      </router-link>
    城市选择</div>
  </div>
</template>

<script>
export default {
  name: 'CityHeader'
}
</script>

<style lang="stylus" scoped>
@import '~styles/iconfont/variable.styl'
.header
  position relative
  height $HeaderHeight
  line-height $HeaderHeight
  color #fff
  font-size .32rem
  text-align center
  background $bgColor
  .header-back
    position absolute
    width .8rem
    font-weight bold
    color #fff
</style>
