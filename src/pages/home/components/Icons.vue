<template>
  <div class="icons-wrapper">
    <ul class="icons">
        <li class="icon">
          <div class="icon-img classify">
          </div>
          <p class="icon-desc">分类</p>
        </li>
        <li class="icon">
          <div class="icon-img ranking">
          </div>
          <p class="icon-desc">排行</p>
        </li>
        <li class="icon" >
          <div class="icon-img follow">
          </div>
          <p class="icon-desc">追更</p>
        </li>
        <li class="icon">
          <div class="icon-img history">
          </div>
          <p class="icon-desc">历史</p>
        </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Icons',
  props: {
    list: Array
  },
  data() {
    return {
      swiperOption: {}
    }
  },
  computed: {
    pages() {
      const pages = []
      this.list.forEach((item, index) => {
        // 如果超出 8 个, 超出的第一个下标是 8, 8 / 8 = 1
        const page = Math.floor(index / 8)
        // 单页初始化，创建一个空数组
        if(!pages[page]) {
          pages[page] = []
        }
        // 将 iconList push 进去
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>

<style scoped lang="stylus">
  @import '~styles/varibles.styl'
  @import '~styles/mixins.styl'
  .icons-wrapper
    z-index: 5
    position: relative
    .icons
      display: flex
      justify-content: center
      height: 2.5rem
      width: 100%
      background-image: url('../../../../static/icons/波浪.png')
      background-size: 100% 2rem
      background-attachment: scroll
      background-repeat: no-repeat
      background-color: transparent
      margin-top: -.6rem
      z-index: 5
      .icon
        display: flex
        flex-direction: column
        justify-content: center
        align-items: center
        width: 22%
        height: 3rem
        .icon-img
          width: 1rem
          height: 1rem
          background-image: url('../../../../static/icons/sprite.png')
          background-repeat: no-repeat
          background-size: 8.6rem 4rem
        .icon-img.classify
          background-position: -1.12rem -2.9rem
        .icon-img.ranking
          background-position: -0.01rem -3rem
        .icon-img.follow
          background-position: -4.76rem -1.4rem
        .icon-img.history
          background-position: -3.62rem -1.4rem
        .icon-desc
          height: 0.5rem;
          line-height: 0.5rem;
          font-size: 0.2rem;
          color: #969696;
          text-align: center;
          overflow: hidden;
          white-space: nowrap;
          text-overflow: ellipsis;
          margin-top: .05rem;
</style>
