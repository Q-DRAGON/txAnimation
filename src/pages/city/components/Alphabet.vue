<template>
  <ul class="list">
    <li
    class="item"
    v-for="item in letters"
    :key="item"
    :ref="item"
    @touchstart="handleTouchStart"
    @touchmove="handleTouchMove"
    @touchend="handleTouchEnd"
    @click="handleLetterClick"
    >
    {{item}}</li>
  </ul>
</template>

<script>

export default {
  name: 'CityAlphabet',
  props: {
    cities: Object
  },
  computed: {
    letters() {
      // 拿到 [A, B, C ...] 的数组
      const letters = []
      for(let i in this.cities) {
        letters.push(i)
      }
      return letters
    }
  },
  data() {
    return {
      touchStatus: false,
      startY: 0
    }
  },
  updated() {
    this.startY = this.$refs['A'][0].offsetTop
  },
  methods: {
    handleLetterClick(e) {
      // A 元素和绿色底部的距离
      this.$emit('change', e.target.innerText)
    },
    handleTouchStart() {
      this.touchStatus = true
    },
    handleTouchMove(e) {
      // 获取手指和高度的差值, 除以每个字母的高度，得到现在的字母
      if(this.touchStatus) {
        if(this.timer) {
          clearTimeout(this.timer)
        }
        // 延迟 16 毫秒后再执行。节流（节省执行频率）
        this.timer = setTimeout(() => {
          // 手指位置和绿色底部的距离
          const touchY = e.touches[0].clientY - 79
          // (手指和绿底的距离 - A 元素和绿底的距离) / 每个字母的高度
          // = (手指位置距离字母表顶部的距离) / 每个字母的高度
          // 得到手指位置处在字母表的第几个/下标
          const index = Math.floor((touchY - this.startY) / 20)
          if(index >= 0 && index < this.letters.length) {
            this.$emit('change', this.letters[index])
          }
        }, 16)
      }
    },
    handleTouchEnd() {
      this.touchStatus = false
    }
  }
}
</script>

<style scoped lang="stylus">
  @import '~styles/varibles.styl'
  .list
    touch-action: none
    display: flex
    flex-direction: column
    justify-content: center
    position: absolute
    top: 1.58rem
    right: 0
    bottom: 0
    width: .4rem
    .item
      line-height: .4rem
      text-align: center
      color: $bgColor
</style>
