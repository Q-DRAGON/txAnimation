<template>
  <ul class="recommend">
    <li class="comic-item">
      <a class="comic-link" href="/comic/index/id/628409?trace_id=2_911_10.239.194.211_1525361809" data-id="628409" data-trace-id="2_911_10.239.194.211_1525361809" data-reportstr="comic_info.628409">
        <div class="comic-cover">
          <img class="comic-image" src="https://manhua.qpic.cn/vertical/0/13_17_32_7c37ccadfe4a0597fdfb4e2d3e1f4ff1_1520933557657.jpg/210">
        </div>
        <div class="comic-info">
          <p class="comic-title">纯情丫头：霸少宠上天</p>
          <p class="comic-desc">家族企业深陷债务危机</p>
        </div>
      </a>
    </li>
    <li class="comic-item">
      <a class="comic-link" href="/comic/index/id/622103?trace_id=2_911_10.239.194.211_1525361809" data-id="622103" data-trace-id="2_911_10.239.194.211_1525361809" data-reportstr="comic_info.622103">
        <div class="comic-cover">
          <img class="comic-image" src="https://manhua.qpic.cn/vertical/0/10_14_59_814d608f698fc743a094d4c56e8a41aa_1520665149826.jpg/210">
        </div>
        <div class="comic-info">
          <p class="comic-title">霸道女总成长记</p>
          <p class="comic-desc">霸道女总VS各路男神</p>
        </div>
      </a>
    </li>
    <li class="comic-item">
      <a class="comic-link" href="/comic/index/id/632194?trace_id=2_911_10.239.194.211_1525361809" data-id="632194" data-trace-id="2_911_10.239.194.211_1525361809" data-reportstr="comic_info.632194">
        <div class="comic-cover">
          <img class="comic-image" src="https://manhua.qpic.cn/vertical/0/26_10_56_c883c259e27b1c81d13a1b08788410d5_1522033014522.jpg/210">
        </div>
        <div class="comic-info">
          <p class="comic-title">一笙有喜</p>
          <p class="comic-desc">她是夜城最好最年轻的</p>
        </div>
      </a>
    </li>
  </ul>
</template>

<script>
  export default {
    name: "DetailRecommend"
  }
</script>

<style scoped lang="stylus">
  @import '~styles/mixins.styl'
  .recommend
    width: 100%
    display: inline-block
    margin-bottom: 2rem
    .comic-item
      float:left
      overflow: hidden
      display: flex
      flex-direction: column
      width: 28%
      height: 5rem
      margin-left: .4rem
      margin-top: .1rem
      background: #F5F5EE;
      .comic-cover
          width: 100%
        .comic-image
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
