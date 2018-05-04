<template>
  <div class="list" ref="wrapper">
    <div class="search-hot-npc">
        <span class="npc-avatar"></span>
        <span class="npc-dialog"></span>
    </div>
    <ul class="search-hot-list">
        <li class="item">
          <a class="link" href="#">贩卖大师</a>
        </li>
        <li class="item">
            <a class="link" href="#">败者为寇</a>
        </li>
        <li class="item">
            <a class="link" href="#">江少要不要嫁过来</a>
        </li>
        <li class="item">
            <a class="link" href="#">狗城</a>
        </li>
        <li class="item">
            <a class="link" href="#">武炼巅峰</a>
        </li>
        <li class="item">
            <a class="link" href="#">我是大神仙</a>
        </li>
        <li class="item">
            <a class="link" href="#">末世凡人</a>
        </li>
        <li class="item">
            <a class="link" href="#">天籁音灵</a>
        </li>
        <li class="item">
            <a class="link" href="#">重生只为追影帝</a>
        </li>
        <li class="item">
            <a class="link" href="#">闪婚娇妻</a>
        </li>
    </ul>
  </div>
</template>

<script>
import Bscroll from 'better-scroll'
import { mapState, mapMutations }  from 'vuex'

export default {
  name: 'CityList',
  props: {
    hot: Array,
    cities: Object,
    letter: String
  },
  computed: {
    // 把 store 的 city 映射到这里名为 currentCity
    ...mapState({
      currentCity: 'city'
    })
  },
  methods: {
    handleCityClick(city) {
      this.changeCity(city)
      this.$router.push('/')
    },
    // 把 Mutations 里有个 changeCity 映射到这里
    ...mapMutations(['changeCity'])
  },
  mounted() {
    this.scroll = new Bscroll(this.$refs.wrapper)
  },
  watch: {
    letter() {
      if(this.letter) {
        // 获取被点击的字母的 DOM
        const element = this.$refs[this.letter][0]
        this.scroll.scrollToElement(element)
      }
    }
  }
}
</script>

<style scoped lang="stylus">
  @import '~styles/varibles.styl'
  .search-hot-npc
    display: flex
    align-items: center
    height: 1.6rem
    margin: 0 0.3rem
    border-bottom: 1px solid #C5C5C5
    .npc-avatar
      display: inline-block
      background: url(/static/icons/spriteSearch.png)
      background-position: 0rem -1rem
      background-size: 2.9rem 2.4rem
      background-repeat: no-repeat
      width: 1.1rem
      height: 0.8rem
    .npc-dialog
      display: inline-block
      background: url(/static/icons/spriteSearch.png)
      background-position: 0rem 0.1rem
      background-size: 2.8rem 2.4rem
      background-repeat: no-repeat
      width: 2.8rem
      height: 1rem
  .search-hot-list
    padding: 0.45rem 0.3rem
    font-size: 0
    .item
      display: inline-block
      margin-bottom: 0.25rem
      margin-right: 0.25rem
      .link
        display: inline-block
        padding: 0.4rem .5rem
        border-radius: 2.25rem
        background-color: white
        border: 1px solid #C5C5C5
        font-size: 0.4rem
        color: #535252
    
</style>
