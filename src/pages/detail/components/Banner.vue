<template>
  <div class="banner">
    <img class="banner-img-bg" :src="dataDetail.imgUrl" alt="">
    <div class="banner-img-cover">
      <img class="banner-img" :src="dataDetail.imgUrl" alt="">
    </div>
    <div class="banner-info">
      <ul>
        <li class="banner-info-title">
          <h1 class="banner-info-name">{{dataDetail.title}}</h1>
          <span class="banner-info-grade">8.9</span>
        </li>
        <li class="banner-info-tags">
          <label class="banner-info-label">标签:</label>
          <span>悬疑</span>
          <span>热血</span>
          <span>竞技</span>
        </li>
        <li class="banner-info-author">
          <label class="banner-info-label">作者:</label>
          <span>常盘勇者</span>
        </li>
        <li class="banner-info-hot">
          <label class="banner-info-label">人气:</label>
          <span class="info-number">1516.1万</span>
        </li>
        <li class="banner-info-mt">
          <label class="banner-info-label">月票:</label>
          <span class="info-number">8</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import CommonGallary from 'common/gallary/Gallary'
import FadeAnimation from 'common/fade/FadeAnimation'
import axios from 'axios'

export default {
  name: 'DetailBanner',
  props: {
    sightName: String,
    bannerImg: String,
    bannerImgs: Array,
  },
  data() {
    return {
      showGallary: false,
      dataDetail: ''
    }
  },
  created () {
    this.fetchData()
  },
  watch: {
    // 如果路由有变化，会再次执行该方法
    '$route': 'fetchData'
  },
  methods: {
    handleBannerClick() {
      this.showGallary = true
    },
    handleGallaryClose() {
      this.showGallary = false
    },
    fetchData () {
      this.getDataInfo()
    },
    getDataInfo() {
      axios.get('/api/index.json')
        .then(this.getDataInfoSucc)
    },
    getDataInfoSucc(res) {
      res = res.data
      if(res.ret && res.data) {
        const data = res.data
        this.dataDetail = this.dataFilter(data.recommendList)
      }
    },
    dataFilter(data) {
      // console.log('id', this.$route.params.id)
      for (var i = 0; i < data.length; i++) {
        if(data[i].id == this.$route.params.id) {
          return data[i]
        }
      }
    }
  },
  components: {
    CommonGallary,
    FadeAnimation
  }
}
</script>

<style scoped lang="stylus">
  .banner
    margin-top: 1.3rem
    overflow: hidden
    height: 5.5rem
    position: relative
    .banner-img-bg
      filter: blur(.4rem)
      width: 100%
    .banner-img-cover
      position: absolute
      width: 3.5rem
      height: 4.7rem
      bottom: 0
      left: 1rem
      &:after
        width: 50%
        height: 100%
        display: block
        transform: skew(4deg, 0deg)
        content: ''
        background-color: rgba(0, 0, 0, 0.2)
        position: absolute
        z-index: 2
        right: -0.3rem
        bottom: -0.25rem
        filter: blur(.4rem)
      .banner-img
        position: absolute
        width: 3.5rem
        height: 4.7rem
        z-index: 3
    .banner-info
      display: flex
      position: absolute
      align-items: center
      width: 48%
      right: 0.1rem
      height: 4.75rem
      bottom: 0
      line-height: .52rem
      color: #fff
      .banner-info-title
        display: inline-flex
        justify-content: center
        .banner-info-name
          display: inline-block
          font-family: $searchFont
          font-weight: 700
          font-size: 0.5rem
        .banner-info-grade
          display: inline-flex
          justify-content: center
          align-items: center
          margin-left: 0.12rem
          width: 0.55rem
          height: 0.55rem
          background: #d97e5c
          border-radius: 50%
      .banner-info-tags
        padding-top: 0.3rem
        font-size: 0
        label,span
          font-size: 12px
        span
          border-left: 1px solid white
          padding-left: 0.15rem
          padding-right: 0.15rem
          &:nth-of-type(1)
            border-left: none
      .banner-info-label
        padding-right: 0.12rem
      .info-number
        color: #fef886



</style>
