<template>
  <div>
    <home-header/>
    <home-swiper/>
    <home-icons/>
    <home-reconmmend/>
    <home-weekend/>
  </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeReconmmend from './components/Reconmmend'
import HomeWeekend from './components/Weekend'

export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeReconmmend,
    HomeWeekend
  }

}
</script>

<style scoped>

</style>
