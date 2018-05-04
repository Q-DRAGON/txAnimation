<template>
  <div>
    <detail-header></detail-header>
    <detail-banner
    :bannerImg="bannerImg"
    :bannerImgs="gallaryImgs"
    :sightName="sightName"
    ></detail-banner>
    <detail-list :list="list" @tabSwitch="recommendShow"></detail-list>
    <detail-recommend v-show="isRecommendShow !== 'comment'"></detail-recommend>
    <detail-tool-bar></detail-tool-bar>
    <detail-drop></detail-drop>
  </div>
</template>

<script>
import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'
import DetailList from './components/List'
import DetailRecommend from './components/Recommend'
import DetailToolBar from './components/ToolBar'
import DetailDrop from 'common/drop/Drop'
import axios from 'axios'

const debug = process.env.NODE_ENV !== 'production';

export default {
  name: 'Detail',
  components: {
    DetailBanner,
    DetailHeader,
    DetailList,
    DetailDrop,
    DetailRecommend,
    DetailToolBar
  },
  data() {
    return {
      sightName: '',
      bannerImg: '',
      gallaryImgs: [],
      list: [],
      isRecommendShow: true
    }
  },
  methods: {
    getDetailInfo() {
      const url = debug ? '/api/detail.json' : 'https://raw.githubusercontent.com/Q-DRAGON/txAnimation/master/dist/static/mock/detail.json'
      axios.get(url)
        .then(this.handleGetDataSucc)
    },
    handleGetDataSucc(res) {
      res = res.data
      if(res.ret && res.data) {
        const data = res.data
        this.sightName = data.sightName
        this.bannerImg = data.bannerImg
        this.gallaryImgs = data.gallaryImgs
        this.list = data.categoryList
      }
    },
    recommendShow(tab) {
      this.isRecommendShow = tab
    }
  },
  mounted() {
    this.getDetailInfo()
  }
}
</script>

<style scoped lang="stylus">
  .content
    height: 50rem
</style>
