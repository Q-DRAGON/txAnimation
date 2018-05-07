<template>
<div class="header-wrapper">
    <div class="header">
      <router-link to="/">
        <div class="iconfont header-back">&#xe63f;</div>
      </router-link>
    <div class="search">
      <input v-model="keyword" class="search-input" type="text" ref="input" @focus="focusSearchIcon" @blur="blurSearchIcon">
      <div class="search-placeholder">
        <span class="search-icon" :class="{ offsetLeft: isoffsetLeft }"></span>
        <span class="search-hint-txt" :class="{ hide: isoffsetLeft }">漫画名|作者</span>
      </div>
        <span class="search-clear" :class="{ hide: !isoffsetLeft }" @click="blurSearch"></span>
    </div>
      <input class="search-submit" type="submit" value="搜索">
    </div>
    <div class="search-content" ref="search" v-show="keyword">
    <ul>
      <li class="search-item border-bottom"
      v-for="item of list"
      :key="item.id"
      @click="handleNameClick(item.name)"
      >{{item.name}}</li>
      <li class="search-item border-bottom" v-show="hasNodata">没有找到匹配数据</li>
    </ul>
  </div>
</div>
</template>

<script>
import Bscroll from 'better-scroll'
import { mapMutations }  from 'vuex'

export default {
  name: 'CityHeader',
    props: {
    cities: Object
  },
  data() {
    return {
      keyword: '',
      list: [],
      timer: null,
      isoffsetLeft: false
    }
  },
  methods: {
    handleNameClick(name) {
      this.keyword = name
    },
    focusSearchIcon() {
      this.isoffsetLeft = true
    },
    blurSearchIcon() {
      if(this.keyword == "") {
        this.isoffsetLeft = false
      }
    },
    blurSearch() {
      this.keyword = ""
      this.blurSearchIcon()
      this.$refs.input.blur()
    }
  },
  computed: {
    hasNodata() {
      return !this.list.length
    }
  },
  watch: {
    keyword() {
      if(this.timer) {
        clearTimeout(this.timer)
      }
      // 输入框没有值时取消显示
      if(!this.keyword) {
        this.list = []
        return
      }
      this.timer = setTimeout(() => {
        const result = []
        for(let i in this.cities) {
          // 遍历每个字母域下的所有城市
          this.cities[i].forEach((value) => {
            // 输入内容和遍历出的 value 配对, 如果配对成功, indexOf 会大于 -1（-1 则是完全不匹配）
            if(value.spell.indexOf(this.keyword) > -1 || value.name.indexOf(this.keyword) > -1) {
              // 把匹配成功的 value push 进 result
              result.push(value)
            }
          })
        }
        this.list = result
      }, 100)
    }
  },
  mounted() {
    this.scroll = new Bscroll(this.$refs.search)
  }
}
</script>

<style scoped lang="stylus">
  @import '~styles/varibles.styl'
  .offsetLeft
    transform: translateX(-2.3rem)
  .hide
    opacity: 0
    visibility: hidden
  .header
    display: flex
    position: relative
    align-items: center
    overflow: hidden
    height: 1.3rem
    line-height: 1.3rem
    text-align: center
    color: #fff
    background: #ff9a6a
    font-size: .32rem
    .header-back
      width: .4rem
      padding: 0 .35rem
      text-align: center
      font-size: .5rem
      color: #fff
    .search
      flex: 1
      touch-action: none
      padding: 0 0 0 .1rem
      position: relative
    .search-placeholder
      display: flex
      align-items: center
      justify-content: center
      position: absolute
      width: 100%
      bottom: 0
      color: #C5C5C5
      font-size: 0.4rem
      pointer-events:none
      .search-icon
        display: inline-block
        background: url(../../../../static/icons/spriteSearch.png)
        background-position: -2.1rem -1rem
        background-size: 2.9rem 2.4rem
        background-repeat: no-repeat
        width: 0.5rem
        height: 0.5rem
        transition: transform 200ms ease
      .search-hint-txt
        transition: all 200ms ease
    .search-clear
      display: inline-block
      width: 0.5rem
      height: 0.5rem
      background: url(../../../../static/icons/spriteSearch.png)
      background-position: -0rem -1.92rem
      background-size: 2.9rem 2.4rem
      background-repeat: no-repeat
      position: absolute
      right: 0.1rem
      bottom: 50%
      transform: translateY(50%)
    .search-input
      width: 100%
      box-sizing: border-box
      height: .85rem
      padding: 0 .1rem 0 .76rem
      line-height: .85rem
      font-size: .4rem
      color: #535252;
      font-family: $searchFont
      border-radius: 0.06rem
  .search-content
    overflow: hidden
    position: absolute
    top: 1.3rem
    width: 100%
    left: 0
    right: 0
    bottom: 0
    background: #eee
    z-index: 999
    .search-item
      line-height: .62rem
      padding-left: .2rem
      background: #fff
      color: #666
  .search-submit
    padding: 0.3rem
    font-size: 0.4rem
    color: white
    border: 0 none
    background: transparent
    font-family: $searchFont
</style>
