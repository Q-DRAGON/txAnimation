<template>
  <div class="wrapper">
    <swiper :options="swiperOption" v-if="showSwiper">
      <swiper-slide v-for="(item, index) of list" :key="item.id">
        <img class="swiper-img" :src="item.imgUrl">
      </swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
  export default {
    name: 'HomeSwiper',
    props: {
      list: Array
    },
    data() {
      return {
        swiperOption: {
          loop: true,
          autoplay: 3000,
          autoplayDisableOnInteraction : false,
          pagination: '.swiper-pagination',
          paginationBulletRender(swiper, index, className) {
            return '<span class="' + className + '">' + '</span>'
          }
        }
      }
    },
    computed: {
      showSwiper() {
        return this.list.length
      }
    }
  }
</script>

<style scoped lang="stylus">
  .wrapper >>> .swiper-pagination-bullets
    width: 95%
    margin: 0 10px
    text-align: right
  .wrapper >>> .swiper-pagination-bullet
    width: 0.13rem
    height: 0.13rem
    border-radius: 0.13rem
    margin: 0rem
    margin-left: 0.1rem
    background: #F5F5EE
    opacity: 1
    transition: width 300ms ease, background 300ms ease
  .wrapper >>> .swiper-pagination-bullet.swiper-pagination-bullet-active 
    background: #ff9a6a
    width: 0.4rem
    z-index: 1
  .wrapper
    position: relative
    z-index: 1
    margin-top: 1rem
    overflow: hidden
    width: 100%
    height: 0
    padding-bottom: 58.13%
    background: #eee
    .swiper-img
      width: 100% 
</style>
