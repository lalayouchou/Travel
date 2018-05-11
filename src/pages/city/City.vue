<template>
  <div>
    <city-header></city-header>
    <city-search></city-search>
    <city-list
    :cities="cities"
    :hotCities="hotCities"
    :letter="letter"
    ></city-list>
    <city-alphabet :cities="cities" @change="HandleChangeLetter"></city-alphabet>
  </div>
</template>

<script>
import CityHeader from './components/Header.vue'
import CitySearch from './components/Search.vue'
import CityList from './components/List.vue'
import CityAlphabet from './components/Alphabet.vue'
import axios from 'axios'
export default {
  name: 'City',
  components: {
    CityHeader,
    CitySearch,
    CityList,
    CityAlphabet
  },
  mounted () {
    this.getCityInfo()
  },
  data () {
    return {
      cities: {},
      hotCities: {},
      letter: ''
    }
  },
  methods: {
    getCityInfo () {
      axios.get('/api/city.json')
        .then(this.getCityInfoSucc)
        .catch(this.getCityInfoFail)
    },
    getCityInfoSucc (msg) {
      msg = msg.data
      if (msg.ret && msg.data) {
        const data = msg.data
        this.cities = data.cities
        this.hotCities = data.hotCities
      }
    },
    getCityInfoFail (err) {
      console.log(err)
    },
    HandleChangeLetter (msg) {
      this.letter = msg
    }
  }
}
</script>

<style lang="stylus" scoped>

</style>
