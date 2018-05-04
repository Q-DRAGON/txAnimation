<template>
  <div>
    <div class="daily-update-title">
      <strong class="title-content"></strong>
      <span class="link-more"></span>
    </div>
    <div class="daily-update">
      <div class="daily-update-aside"></div>
      <ul class="comic-wrapper">
        <router-link
        tag="li"
        class="comic border"
        v-for="(item, index) of list"
        :key="item.id"
        :to="`/detail/${item.id}`">
            <div class="comic-cover">
              <img class="comic-img" :src="item.imgUrl">
            </div>
            <div class="comic-info">
              <p class="comic-title">{{item.title}}</p>
              <p class="comic-aritist">{{item.aritist}}</p>
              <p class="comic-lastest">{{item.lastest}}</p>
              <div class="comic-rank-wrapper">
                <span class="comic-rank-bar" v-for="item in rank[index]"></span>
              </div>
              <p class="comic-score">{{item.score}}</p>
            </div>
        </router-link>
      </ul>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'HomeRecommend',
    props: {
      list: Array,
      rank: Array
    }
  }
</script>

<style scoped lang="stylus">
  @import '~styles/mixins.styl'
  .dailyPush-title
    height: 1.4rem
    background: #F5F5EE
    text-indent: .2rem
  .title-content
    width: 4rem
    height: 1.4rem
    display: inline-block
    background: url("/static/icons/spriteTittle.png")
    background-position: -2.5rem -3.5rem
    background-repeat: no-repeat
    background-size: 11rem 9.5rem
  .link-more
    float: right
    width: 1.6rem
    height: 0.7rem
    background: url("/static/icons/spriteTittle.png")
    background-position: -9.1rem -1.25rem
    background-repeat: no-repeat
    background-size: 11rem 9.5rem
    margin-top: 0.5rem
    margin-right: 0.3rem
  .daily-update
    display: flex
    background: #fff
    .daily-update-aside
      display: inline-block
      width: 2.7rem
      height: 9.5rem
      background: url("/static/icons/spriteTittle.png")
      background-position: 0rem 0.3rem
      background-repeat: no-repeat
      background-size: 11rem 9.5rem
    .comic-wrapper
      flex: 1
      .comic
        background: #F5F5EE
        display: flex
        flex-direction: row
        height: 2.8rem
        margin-right: .3rem
        margin-bottom: .3rem 
        .comic-cover
          width: 2.15rem
          .comic-img
            width: 100%
            height: 100%
        .comic-info
          flex: 1
          .comic-title
            margin-top: 0.3rem
            margin-left: 0.3rem
            font-size: 0.45rem
            font-weight: bold
            color: #535252
          .comic-aritist
            margin-top: 0.2rem
            margin-left: 0.3rem
            font-size: 0.2rem
            font-weight: normal
            color:  #969696
          .comic-lastest
            margin-top: 0.2rem
            margin-left: 0.3rem
            font-size: 0.2rem
            font-weight: normal
            color:  #969696
          .comic-rank-wrapper
            margin-left: 0.3rem
            display: inline-block
          .comic-rank-bar
            display: inline-block
            margin-top: 0.2rem
            width: 0.3rem
            height: 0.3rem
            background: url(/static/icons/spriteTittle.png)
            background-position: -10.66rem -2rem
            background-repeat: no-repeat
            background-size: 11rem 9.5rem
          .comic-score
            display: inline-block
            color: #ff9a6a
</style>
