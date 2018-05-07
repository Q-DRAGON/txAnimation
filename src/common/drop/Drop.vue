<template>
<transition name="drop-container">
  <div class="drop-wrapper" v-show="isDropShow">
    <transition name="drop-nav">
      <div class="drop-list" v-show="isDropShow">
        <ul class="nav-list">
          <li class="nav-item">
            <div class="item-icon icon-home"></div>
            <div class="item-title">首页</div>
          </li>
          <li class="nav-item">
            <div class="item-icon icon-collect"></div>
            <div class="item-title">收藏</div>
          </li>
          <li class="nav-item">
            <div class="item-icon icon-history"></div>
            <div class="item-title">历史</div>
          </li>
          <li class="nav-item">
            <div class="item-icon icon-classify"></div>
            <div class="item-title">分类</div>
          </li>
          <li class="nav-item">
            <div class="item-icon icon-ranking"></div>
            <div class="item-title">排行</div>
          </li>
          <li class="nav-item">
            <div class="item-icon icon-follow"></div>
            <div class="item-title">追更</div>
          </li>
        </ul>
        <div class="btn-home"></div>
      </div>
    </transition>
    <transition name="mask">
      <div class="drop-mask" v-show="isDropShow" @click="handleMaskClick"></div>
    </transition> 
  </div>
</transition>
</template>

<script>
import { mapState, mapMutations }  from 'vuex'

  export default {
    name: 'Drop',
    computed: {
      ...mapState(['isDropShow'])
    },
    methods: {
    handleMaskClick() {
      this.changeDropListShow()
    },
    ...mapMutations(['changeDropListShow'])
   }
  }
</script>

<style scoped lang="stylus">
  @import '~styles/mixins.styl'
  @keyframes hide
    0% { opacity: 1 }
    100% { opacity: 0 }
  @keyframes show
    0% { opacity: 0 }
    100% { opacity: 1 }
  @keyframes down
    0% { top: -5.2rem }
    100% { top: 0rem }
  @keyframes up
    0% { top: 0rem }
    100% { top: -5.2rem }
  .drop-nav-enter-active
    animation: down 300ms ease
  .drop-nav-leave-active
    animation: up 300ms ease
  .mask-enter-active, .drop-container-enter-active
    animation: show 300ms ease
  .mask-leave-active, .drop-container-leave-active
    animation: hide 300ms ease 
  .drop-wrapper
    position: fixed
    z-index: 150
    top: 1.3rem
    width: 100%
    height: 100%
    overflow: hidden
    .drop-list
      display: flex
      position: absolute
      width: 100%
      height: 4.8rem
      z-index: 15
      top: 0rem
      background:#F5F5EE
      flex-direction: column
      padding-bottom: .4rem
      .nav-list
        display: flex
        width: 100%
        justify-content: center
        flex-wrap: wrap
        height: 100%
        .nav-item
          float: left
          width: 32%
          display: flex
          flex-direction: column
          align-items: center
          justify-content: center
          .item-icon
            width: 1rem
            height: 1rem
            background: url("../../../static/icons/sprite.png")
            background-repeat: no-repeat
            background-size: 8.6rem 4rem
          .item-icon.icon-classify
            background-position: -1.12rem -2.9rem
          .item-icon.icon-ranking
            background-position: -0.01rem -3rem
          .item-icon.icon-follow
            background-position: -4.76rem -1.4rem
          .item-icon.icon-history
            background-position: -3.62rem -1.4rem
          .item-icon.icon-home
            background-position: -5.9rem -1.4rem
          .item-icon.icon-collect
            background-position: -7.02rem -1.4rem
          .item-title
            margin-top: 0.1rem
            font-size: 0.2rem
            color: #969696
            white-space: nowrap
            text-overflow: ellipsis
      .btn-home
        width: 8rem;
        height: 1.65rem
        margin: 0 auto
        background: url(../../../static/icons/sprite.png)
        background-repeat: no-repeat
        background-position: 0rem 0rem
        background-size: 8rem 3.7rem
    .drop-mask
      width: 100%
      height: 100%
      z-index: 150
      top: 1.3rem
      background: rgba(0, 0, 0, .4)  
</style>
