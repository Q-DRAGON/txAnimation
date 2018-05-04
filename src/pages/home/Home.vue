<template>
  <div class="">
    <home-header :city="city"></home-header>
    <home-swiper :list="swiperList"></home-swiper>
    <home-icons :list="iconList"></home-icons>
    <home-recommend :list="recommendList"></home-recommend>
    <home-daily :list="dailyList"></home-daily>
    <home-weekend :list="weekendList" :rank="rankList"></home-weekend>
    <home-drop></home-drop>
  </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeDaily from './components/Daily'
import HomeWeekend from './components/Weekend'
import HomeDrop from 'common/drop/Drop'

import { mapState } from 'vuex'
import axios from 'axios'

const debug = process.env.NODE_ENV !== 'production';

export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecommend,
    HomeWeekend,
    HomeDaily,
    HomeDrop
  },
  data() {
    return {
      lastCity: '',
      swiperList: [],
      iconList: [],
      recommendList: [],
      dailyList: {},
      weekendList: [],
      rankList: []
    }
  },
  computed: {
    ...mapState(['city'])
  },
  methods: {
    getHomeInfo() {
      const url = debug ? '/api/index.json' : 'https://raw.githubusercontent.com/Q-DRAGON/txAnimation/master/dist/static/mock/home.json'
      axios.get(url)
        .then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc(res) {
      res = res.data
      if(res.ret && res.data) {
        const data = res.data
        this.swiperList = data.swiperList
        this.iconList = data.iconList
        this.dailyList = data.dailyList
        this.recommendList = data.recommendList
        this.weekendList = data.weekendList
        this.rankList = this.getRankCount()
      }
    },
    getRankCount() {
       let rankArray = []
      for(let i = 0; i < this.weekendList.length; i++) {
          let score = this.weekendList[i].score
          if(score > 8) {
            rankArray.push(5)
          } else if (score > 6 && score < 8) {
            rankArray.push(4)
          } else if (score > 4 && score < 6) {
            rankArray.push(3)
          } else if (score > 2 && score < 4) {
            rankArray.push(2)
          } else {
            rankArray.push(1)
          }
      }
      return rankArray
    }
  },
  mounted() {
    this.lastCity = this.city
    this.getHomeInfo()
  },
  // 由于有了 keep-alive, 重新加载页面时，我们需要检查城市是否变化，如果变化就重新发送请求
  activated() {
    if(this.lastCity !== this.city) {
      this.lastCity = this.city
      this.getHomeInfo()
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang='stylus'>
</style>
