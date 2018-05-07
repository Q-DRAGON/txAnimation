<template>
  <div class="dailyPush">
    <div class="dailyPush-title">
      <strong class="title-content"></strong>
      <span class="link-more"></span>
    </div>
    <div class="dailyPush-comic-wrapper">
        <div class="dailyPush-cover">
            <img class="dailyPush-image" :src="list.imgUrl">
        </div>
        <div class="dailyPush-info">
            <p class="info-title info-detail">{{list.title}}</p>
            <p class="info-artist info-detail">{{list.artist}}</p>
        </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'HomeDaily',
    props: {
      list: Object
    }
  }
</script>

<style scoped lang="stylus">
  @import '~styles/mixins.styl'
    .dailyPush
      width: 100%
      background: #F5F5EE
      .dailyPush-title
        height: 1.4rem
        background: #F5F5EE
        text-indent: .2rem
        .title-content
          width: 4rem
          height: 1.4rem
          display: inline-block
          background: url("../../../../static/icons/spriteTittle.png")
          background-position: -7rem 0.3rem
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
      .dailyPush-comic-wrapper
        margin: 0 .3rem
        height: 6rem
        .dailyPush-cover
          width:100%
          .dailyPush-image
            width:100%
            height: 5rem
        .dailyPush-info
          display: flex
          width: 100%
          background: #fff
          .info-detail
            line-height: 1rem
          .info-detail.info-title
            flex: 1
            font-size: 0.45rem
            margin-left: 0.4rem
            color: #535252
          .info-detail.info-artist
            color: #C5C5C5
            margin-right: 0.4rem
</style>
