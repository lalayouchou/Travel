<template>
  <div>
    <div class="search">
      <input type="text" class="search-input" placeholder="输入城市名或拼音">
    </div>
  </div>
</template>

<script>
export default {
  name: 'CitySearch'
}
</script>

<style lang="stylus" scoped>
@import '~styles/iconfont/variable.styl'
.search
  background $bgColor
  height .78rem
  overflow hidden
  .search-input
   display block
   width 90%
   margin auto
   height .55rem
   margin-top .11rem
   text-align center
   border-radius .05rem
   font-size .2rem
   padding 0 .1rem
   color #666
</style>
