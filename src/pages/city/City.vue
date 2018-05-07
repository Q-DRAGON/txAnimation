<template>
  <div>
    <city-header :cities="cities"></city-header>
    <city-list :cities="cities" :hot="hotCities" :letter="letter"></city-list>
  </div>
</template>

<script>
import CityHeader from './components/Header'
import CityList from './components/List'
import axios from 'axios'

const debug = process.env.NODE_ENV !== 'production';

export default {
  name: 'City',
  components: {
    CityHeader,
    CityList
  },
  data() {
    return {
      cities: {},
      hotCities: [],
      letter: '',
      timer: null
    }
  },
  methods: {
    getCityInfo() {
      const url = debug ? '/api/city.json' : 'https://raw.githubusercontent.com/Q-DRAGON/txAnimation/master/dist/static/mock/detail.json'
      axios.get(url)
        .then(this.getCityInfoSucc)
    },
    getCityInfoSucc(res) {
      res = res.data
      if(res.ret && res.data) {
        const data = res.data
        this.cities = data.cities
        this.hotCities = data.hotCities
      }
    },
    handleLetterChange(letter) {
      this.letter = letter
    }
  },
  mounted() {
    this.getCityInfo()
  }
}
</script>

<style scoped lang="stylus">
</style>
