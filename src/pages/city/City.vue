<template>
  <div>
    <city-header/>
    <city-search/>
    <city-list :cities="cities" :hotCities="hotCities" :letter="letter"/>
    <city-alphabet :cities="cities" @change="handleLetterChange" />
  </div>
</template>

<script>
import axios from 'axios'
import CityHeader from './components/Header'
import CitySearch from './components/Search'
import CityList from './components/List'
import CityAlphabet from './components/Alphabet'

export default {
  name: 'City',
  components: {
    CityHeader,
    CitySearch,
    CityList,
    CityAlphabet
  },
  data () {
    return {
      cities: {},
      hotCities: [],
      letter: ''
    }
  },
  methods: {
    handleLetterChange (letter) {
      this.letter = letter
    },
    getCityInfo () {
      axios.get('/static/mock/city.json').then(this.handleGetCityInfoSuccess)
    },
    handleGetCityInfoSuccess (result) {
      console.log(result)
      result = result.data
      if (result.ret && result.data) {
        const data = result.data
        this.cities = data.cities
        this.hotCities = data.hotCities
      }
    }
  },
  mounted () {
    this.getCityInfo()
  }

}
</script>

<style lang="stylus" scoped>

</style>
