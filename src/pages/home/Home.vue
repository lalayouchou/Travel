<template>
  <div>
    <home-header></home-header>
    <home-swiper></home-swiper>
  </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper.vue'
export default {
  name: 'Home',
  components: {
    HomeSwiper,
    HomeHeader
  }
}
</script>

<style>

</style>
