<template>
  <div>
    <detail-banner
    :gallery="gallery"
    :bannerImg="bannerImg"
    :sightName="sightName"
    ></detail-banner>
    <div class="content">
      <detail-list :list="list"></detail-list>
    </div>
  </div>
</template>

<script>
import DetailBanner from './components/Banner.vue'
import DetailList from './components/List.vue'
import axios from 'axios'
export default {
  name: 'Detail',
  components: {
    DetailBanner,
    DetailList
  },
  data () {
    return {
      list: [],
      gallery: [],
      bannerImg: '',
      sightName: '',
      lastId: ''
    }
  },
  mounted () {
    this.getDetailInfo()
    this.lastId = this.$route.params.id
  },
  activated () {
    if (this.lastId !== this.$route.params.id) {
      this.getDetailInfo()
      this.lastId = this.$route.params.id
      console.log('1')
    }
  },
  methods: {
    getDetailInfo () {
      axios.get('/api/detail.json', {
        params: {
          id: this.$route.params.id
        }
      }).then(this.getDetailInfoSucc)
        .catch(this.getDetailInfoFail)
    },
    getDetailInfoSucc (msg) {
      msg = msg.data
      if (msg.ret && msg.data) {
        const data = msg.data
        this.bannerImg = data.bannerImg
        this.sightName = data.sightName
        this.gallery = data.gallaryImgs
        this.list = data.categoryList
      }
    },
    getDetailInfoFail (e) {
      console.log(e)
    }
  }
}
</script>

<style lang="stylus" scoped>
.content
  height 50rem
</style>
