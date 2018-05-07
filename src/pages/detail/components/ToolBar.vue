<template>
  <div class="toolBar-flex border-top">
      <div class="toolBar-box">
          <span class="box-btn box-btn-toolFav"></span>
          <span class="box-btn box-btn-toolShare"></span>
          <span class="box-btn box-btn-toolDownload"></span>
      </div>
      <a class="toolBar-toolRead" href="#">开始阅读</a>
  </div>
</template>

<script>
  export default {
    name: 'DetailToolBar'
  }
</script>

<style scoped lang="stylus">
  .toolBar-flex
    display: flex
    justify-content: space-between
    align-items: center
    position: fixed
    bottom: 0
    width: 100%
    height: 1.7rem
    z-index: 9
    background: #fff
    .toolBar-box
      font-size: 0
      .box-btn
        display: inline-block
        width: 0.75rem
        height: 0.75rem
        background: url(../../../../static/icons/spriteLay.png)
        background-size: 2.66rem 1.8rem
        background-repeat: no-repeat
        margin-left: 0.7rem
      .box-btn-toolFav
        background-position: -0.01rem -1.1rem
      .box-btn-toolShare
        background-position: -0.88rem -1.1rem
      .box-btn-toolDownload
        background-position: -1.91rem 0rem
    .toolBar-toolRead
      flex: 1
      height: 1.2rem
      line-height: 1.2rem
      font-size: 0.48rem
      font-weight: bold
      color: white
      background-color: #ff9a6a
      text-align: center
      margin-left: 0.7rem
      margin-right: 0.4rem
</style>
