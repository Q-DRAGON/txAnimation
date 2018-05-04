<template>
  <div>
    <div class="tab-list border-bottom">
      <a href="#" class="tab-list-item" :class="{itemActive: tabShow === 'detail'}" @click="handleTabClick('detail')">详情</a>
      <a href="#" class="tab-list-item" :class="{itemActive: tabShow === 'catalog'}" @click="handleTabClick('catalog')">目录</a>
      <a href="#" class="tab-list-item" :class="{itemActive: tabShow === 'comment'}" @click="handleTabClick('comment')">评论</a>
    </div>
    <div class="mod-wrapper">
      <div class="mod-detail" v-show="tabShow === 'detail'">
        <i class="mod-detail-icon iconfont">&#xe67b;</i>
        <p class="mod-detail-content">
          妖怪从魔界跑到人间骚扰人类，一部分人类学会了除妖术对付妖怪，这些人被称为除妖特工。主角东方鸣是个刚出道的除妖特工，他办事鲁莽，任意妄为。他是个孤儿，是小太阳孤儿院把他养大的，东方鸣需要一大笔钱去肩负起孤儿院，那就是参加三年一度的特工真人秀大比拼。
        </p>
      </div>
      <div class="mod-catalog" v-show="tabShow === 'catalog'">
        <div class="comicList-info-layBox">
          <span class="comicList-info-time">2018-05-02</span>
          <span class="comicList-info-update">更新到44话</span>
        </div>
        <ul class="chapter-list" data-vip-free="1">
          <li class="chapter-item" v-for="(item, index) in chapterItem">
            <a class="chapter-link" data-cid="54" data-seq="44" href="#">{{index + 1}}</a>
          </li>
        </ul>
      </div>
      <div class="mod-comment" v-show="tabShow === 'comment'">
          <ul class="mod-comment-list">
            <li class="mod-comment-item border-bottom">
              <div class="comment-item-head">
                <div class="comment-item-head-layLeft">
                    <span class="comment-item-userHead iconfont">&#xe630;</span>
                    <div class="comment-item-head-layBox">
                        <strong class="comment-item-userName">莎娃迪卡</strong>
                        <span class="comment-item-time">
                            2018年3月11日
                        </span>
                    </div>
                </div>
                <div class="comment-item-head-layRight">
                  <a class="comment-item-like unlike" data-commentid="322867">
                    <span class="iconfont unlike">
                        &#xe660;
                    </span>
                    <span class="comment-item-like-count">
                        1
                    </span>
                  </a>
                </div>
              </div>
              <div class="comment-item-content">
                  <p>垂死梦中惊坐起</p>
              </div>
            </li>
          </ul>
          <div class="mod-load-more">
            <div class="mlm-status-over" style="display: block;">
                客官，人家已经没有那个的啦~~
            </div>
          </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'DetailList',
  props: {
    list: Array,
  },
  data() {
    return {
      chapterItem: 10,
      tabShow: 'detail',
      dataDetail: ''
    }
  },
  methods: {
    handleTabClick(tab) {
      this.tabShow = tab
      this.$emit("tabSwitch", tab)
    }
  }
}
</script>

<style scoped lang="stylus">
  @import '~styles/varibles.styl'
  .tab-list
    display: flex
    .tab-list-item
      display: block
      position: relative
      width: 3.75rem
      height: 1.25rem
      text-align: center
      line-height: 1.25rem
      font-size: 0.35rem
      color: #969696
    .itemActive
      color: #535252
      &:after
        display: block
        content: ''
        width: 0.3rem
        height: 0.08rem
        margin-left: 1.5rem
        bottom: 0
        position: absolute
        background-color: #ff9a6a
        border-radius: 0.15rem
  .mod-wrapper
    .mod-catalog
      .comicList-info-layBox
        margin-left: 4%
        padding-top: 0.5rem
        color: #C5C5C5
      .chapter-list
        padding-top: 0.28rem
        .chapter-item
          display: block
          float: left
          width: 28%
          margin-left: 4%
          margin-bottom: 4%
          height: 1.25rem
          line-height: 1.25rem
          border: 1px solid #C5C5C5
          box-sizing: border-box
          overflow: hidden
          background-color: #fff
          color: #535252
          font-size: 0.4rem
          text-align: center
    .mod-detail
      padding: 0 0.6rem
      .mod-detail-icon
        font-size: 0.8rem
        color: #C5C5C5
        text-align: center
        display: block
        padding-bottom: 0.3rem
        padding-top: 0.3rem
      .mod-detail-content
        font-size: 0.36rem
        color: #535252
        line-height: 150%
        padding-bottom: 0.75rem
    .mod-comment
      padding-left: 0.55rem
      padding-right: 0.55rem
      padding-top: 0.25rem
      padding-bottom: 2.75rem
      .mod-comment-list
        .mod-comment-item
          padding-top: 0.4rem
          .comment-item-head
            display: flex
            justify-content: space-between
            align-items: center
            color: #666666
            .comment-item-head-layLeft
              display: flex
              align-items: center
              .comment-item-userHead
                margin-right: 0.1rem
                font-size: 1rem
              .comment-item-userName
                color: #e86a3e
                display: block
                padding-bottom: 0.1rem
                font-weight: 700
                font-size: 0.38rem
              .comment-item-time
                color: #cccccc
                font-size: 0.3rem
          .comment-item-content
            padding-left: 1.1rem
            padding-top: 0.2rem
            padding-bottom: 0.875rem
            font-size: 0.4rem
            color: #535252
            line-height: 150%
            word-break: break-all
      .mod-load-more
        text-align: center
        padding-top: 0.45rem
        padding-bottom: 0.45rem
        color: #9a9a9a
        font-size: 0.2rem
</style>
