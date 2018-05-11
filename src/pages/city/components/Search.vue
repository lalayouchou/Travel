<template>
  <div>
    <div class="search">
      <input
      type="text"
      class="search-input"
      placeholder="输入城市名或拼音"
      v-model="keyword"
      />
    </div>
    <div class="search-content" v-show="keyword" ref="search">
      <ul>
        <li
        class="search-item border-bottom"
        v-for="item of searchlist"
        :key="item.id"
        >{{item.name}}</li>
        <li class="search-item border-bottom" v-show="hasNoData">没有找到匹配数据</li>
      </ul>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
  name: 'CitySearch',
  props: {
    cities: Object
  },
  data () {
    return {
      keyword: '',
      searchlist: [],
      timer: null
    }
  },
  computed:{
    hasNoData () {
      return !this.searchlist.length
    }
  },
  watch: {
    keyword () {
      if(this.timer){
        clearTimeout(this.timer)
      }
      
      this.timer = setTimeout(() => {
        const result = []
        for (let i in this.cities) {
          this.cities[i].forEach((value) => {
            if (value.name.indexOf(this.keyword) > -1||
              value.spell.indexOf(this.keyword) > -1) {
              result.push(value)
            }
          })
        }
        return this.searchlist = result
      },100)
    }
  },
  mounted () {
    this.scroll = new BScroll(this.$refs.search)
  }
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
   margin .11rem auto 0
   height .55rem
   text-align center
   border-radius .05rem
   font-size .2rem
   padding 0 .1rem
   color #666
.search-content
  overflow hidden
  z-index 1
  position absolute
  left 0
  right 0
  bottom 0
  top 1.64rem
  background #fff
  .search-item
    padding-left .3rem
    line-height .55rem
</style>
