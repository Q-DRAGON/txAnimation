<template>
  <div class="header">
    <router-link to="/">
      <div class="iconfont header-back">&#xe63f;</div>
    </router-link>
      <h1 class="top-title">贩卖大师</h1>
      <div class="header-right">
        <router-link class="top-search top-tab" to="/city" tag="span"></router-link>
        <span class="top-menu top-tab" @click="handleMenuClick"></span>
      </div>
  </div>
</template>

<script>
import { mapState, mapMutations }  from 'vuex'

export default {
  name: 'HomeHeader',
  computed: {
    ...mapState(['city'])
  },
  methods: {
    handleMenuClick() {
      this.changeDropListShow()
    },
    ...mapMutations(['changeDropListShow'])
  }
}
</script>

<style scoped lang="stylus">
  @import '~styles/varibles.styl'
  .header
    display: flex
    align-items: center
    background: #fff
    color: #fff
    height: 1.3rem
    justify-content: space-between
    position: fixed
    z-index: 20
    top: 0
    width: 100%
    .header-back
      width: .4rem
      padding: 0 .4rem 0 .25rem
      font-size: .5rem
      color: #ff9a6a
    .top-title
      color:#535252
      font-family: $searchFont
      font-weight: 700
      font-size: 0.48rem
      white-space: nowrap
      text-overflow: ellipsis
    .header-right
      flex :1
      display: flex
      align-items: center
      justify-content: flex-end
      width: 1.04rem
      height: 1.3rem
      padding:  0 .1rem
      color: #fff
      position: relative
      .top-tab
        width: 0.6rem
        height: 0.6rem
        background: url("/static/icons/sprite.png")
        background-repeat: no-repeat
        background-size: 8rem 3.8rem
      .top-menu
        background-position: -3.05rem -2.94rem
        margin-left: 0.5rem
        margin-right: 0.2rem
      .top-search
        background-position: -3.9rem -2.94rem
        margin-left: 0.5rem
</style>
