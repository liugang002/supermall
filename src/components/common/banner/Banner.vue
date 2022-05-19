<template>
  <swiper   :options="swiperOptions">
    <swiper-slide  v-for="(item, index) in newbanners" :key="item.index">
      <a href="">
        <img :src="item.link" alt="" />
      </a>
    </swiper-slide>
    <div class="swiper-pagination" slot="pagination"></div>
    <div class="swiper-button-prev" slot="button-prev"></div>
    <div class="swiper-button-next" slot="button-next"></div>
  </swiper>
</template>

<script>
import { swiper, swiperSlide } from "vue-awesome-swiper";
import "swiper/css/swiper.min.css";

export default {
  name: "index",
  watch:{
      oldbanners(val){
          console.log('banners');
          console.log(val);
          this.newbanners = this.oldbanners
      }
  },
  data() {
    return {
      date: new Date(),
      newbanners:[],
      swiperOptions: {
        autoplay: {
          delay: 2000,
          disableOnInteraction: true,
        },
        loop: true,
        effect: "cube",
        cube: {
          slideShadows: true,
          shadow: true,
          shadowOffset: 100,
          shadowScale: 0.6,
        },
        navigation: {
          nextEl: ".swiper-button-next",
          prevEl: ".swiper-button-prev",
        },
        pagination: {
          el: ".swiper-pagination",
          type: "bullets",
          clickable: true,
          // progressbarOpposite: true,
        },
      },
    };
  },
  props: {
    oldbanners: {
      type: Array,
      default: [],
    },
  },
  components: {
    swiper,
    swiperSlide,
  },
};
</script>

<style scoped>
img{
    width: 100%;
    height: 150px;
}
</style>
