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
              <div class="botton">{{this.city}}</div>
            </div>
          </div>
        </div>
        <div class="area">
          <div class="area-title border-topbottom">
           热门城市
          </div>
          <div class="area-botton">
            <div
            class="botton-wrapper"
            v-for="item of hotCities"
            :key="item.id"
            @click="handleCityClick(item.name)"
            >
              <div class="botton">{{item.name}}</div>
            </div>
          </div>
        </div>
        <div class="area"
        v-for="(value,key) in cities"
        :key="key"
        :ref="key">
          <div class="area-title border-bottom city-title">
           {{key}}
          </div>
          <div class="city-list" v-for="city in value" :key="city.id">
            <div
            class="city border-bottom"
            @click="handleCityClick(city.name)"
            >{{city.name}}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Bscoll from 'better-scroll'
import { mapState, mapMutations } from 'vuex'
export default {
  name: 'CityList',
  props: {
    cities: Object,
    hotCities: [ Array, Object ],
    letter: String
  },
  mounted () {
    this.scroll = new Bscoll(this.$refs.wrapper)
  },
  watch: {
    letter () {
      if (this.letter) {
        const name = this.letter
        const element = this.$refs[name][0]
        this.scroll.scrollToElement(element)
      }
    }
  },
  computed:{
    ...mapState({city:'city'}),
  },
  methods: {
    handleCityClick (name) {
      this.changeCity(name)
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])
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
      color $bgColor
    .city-list
      .city
        padding-left .3rem
        line-height .6rem
</style>
