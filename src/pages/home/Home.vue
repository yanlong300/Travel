<template>
  <div>
    <home-header :city="city" />
    <home-swiper :list="swiperList" />
    <home-icons :list="iconList" />
    <home-reconmmend :list="recommendList"/>
    <home-weekend :list="weekendList"/>
  </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeReconmmend from './components/Reconmmend'
import HomeWeekend from './components/Weekend'
import axios from 'axios'

export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeReconmmend,
    HomeWeekend
  },
  data () {
    return {
      city: '',
      swiperList: [],
      iconList: [],
      recommendList: [],
      weekendList: []

    }
  },
  methods: {
    getHomeInfo () {
      axios.get('/static/mock/index.json').then(this.getHomeInfoSuccess)
    },
    getHomeInfoSuccess (result) {
      result = result.data
      if (result.ret && result.data) {
        const data = result.data
        this.city = data.city
        this.swiperList = data.swiperList
        this.iconList = data.iconList
        this.recommendList = data.recommendList
        this.weekendList = data.weekendList
      }
    }
  },
  mounted () {
    this.getHomeInfo()
  }

}
</script>

<style scoped>

</style>
