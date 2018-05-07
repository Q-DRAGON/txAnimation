<template>
  <div class="recommend">
    <div class="recommend-title">
      <strong class="title-content"></strong>
      <span class="link-more"></span>
    </div>
    <ul class="comic-wrapper">
      <router-link
      tag="li"
      class="comic border"
      v-for="item of list"
      :key="item.id"
      :to="`/detail/${item.id}`">
          <div class="comic-cover">
            <img class="comic-img" :src="item.imgUrl">
          </div>
          <div class="comic-info">
            <p class="comic-title">{{item.title}}</p>
            <p class="comic-desc">{{item.desc}}</p>
          </div>
      </router-link>
    </ul>
  </div>
</template>

<script>
  export default {
    name: 'HomeRecommend',
    props: {
      list: Array
    }
  }
</script>

<style scoped lang="stylus">
  @import '~styles/mixins.styl'
    .recommend
      touch-action: none
      background: #F5F5EE
      .recommend-title
        height: 1.4rem
        background: #F5F5EE
        text-indent: .2rem
        .title-content
          width: 4rem
          height: 1.4rem
          display: inline-block
          background: url("../../../../static/icons/spriteTittle.png")
          background-position: -2.8rem 0.3rem
          background-repeat: no-repeat
          background-size: 11rem 9.5rem
        .link-more
          float: right
          width: 1.6rem
          height: 0.7rem
          background: url("../../../../static/icons/spriteTittle.png")
          background-position: -9.1rem -1.25rem
          background-repeat: no-repeat
          background-size: 11rem 9.5rem
          margin-top: 0.5rem
          margin-right: 0.3rem
      .comic-wrapper
        width: 100%
        display: inline-block
        .comic
          float:left
          overflow: hidden
          display: flex
          flex-direction: column
          width: 28%
          height: 5rem
          margin-left: .4rem
          margin-top: .1rem
          background: #fff
          .comic-cover
              width: 100%
            .comic-img
              width: 100%
              height: 100%
          .comic-info
            margin-top: 0.1rem
            min-width: 0
            .comic-title
              line-height: .54rem
              font-size: .32rem
              font-weight: 700
              font-size: 0.35rem
              color: #535252
              text-align: center
              ellipsis()
            .comic-desc
              line-height: .4rem
              color: #ccc
              text-align: center
              ellipsis()
</style>
