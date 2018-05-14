<template>
  <div>
  <ul class="list">
    <li
    class="item"
    v-for="(value,key) in cities"
    :key="key"
    :ref="key"
    @click="HandleLetterClick"
    @touchstart.prevent="HandleTouchStart"
    @touchmove="HandleTouchMove"
    @touchend="HandleTouchEnd"
    @touchcancel="HandleTouchEnd"
    >
    {{key}}
    </li>
  </ul>
  <div class="letter-info" v-if="touchMoveStatus">{{letter}}</div>
  </div>
</template>

<script>
export default {
  name: 'CityAlphabet',
  props: {
    cities: Object
  },
  data () {
    return {
      touchStatus: false,
      touchMoveStatus: false,
      letter: '',
      clientY: '',
      timer: null
    }
  },
  computed: {
    letters () {
      return Object.keys(this.cities)
    }
  },
  updated () {
    if (this.startY) return
    this.startY = this.$refs['A'][0].offsetTop
  },
  methods: {
    HandleLetterClick (e) {
      this.$emit('change', e.target.innerText)
      console.log(this.letters)
    },
    HandleTouchStart () {
      this.touchStatus = true
    },
    HandleTouchMove (e) {
      if (this.touchStatus) {
        // 思想：获取A的偏移量，获取touchmove事件的手指在可视区域的位置，减去头部距离
        // ，就是手指距离A的偏移量，除以每个字母的高度，向下取整，就是字母的索引
        if (this.timer) return

        this.timer = setTimeout(() => {
          this.touchMoveStatus = true
          const moveY = e.touches[0].clientY - 82
          const index = Math.floor((moveY - this.startY) / 20)
          if (index >= 0 && index < this.letters.length) {
            this.letter = this.letters[index]
            this.$emit('change', this.letter)
          }

          this.timer = null
        }, 16)
      }
    },
    HandleTouchEnd () {
      setTimeout(() => {
        this.touchStatus = false
        this.touchMoveStatus = false
      }, 16)
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/iconfont/variable.styl'
.list
  position absolute
  right 0
  bottom 0
  top 1.64rem
  width .4rem
  display flex
  flex-direction column
  justify-content center
  // flex-flow row wrap
  // align-content center
  .item
    // width 100%
    line-height .4rem
    text-align center
    color $bgColor
.letter-info
  width: 1rem
  height 1rem
  background $bgColor
  color #fff
  position absolute
  bottom 0
  top 1.64rem
  margin auto 0
  right .8rem
  border-radius 50%
  line-height 1rem
  font-size .5rem
  text-align center
</style>
