<template>
  <div>

    <swiper
    :slides-per-view="3"
    :space-between="50"
    @swiper="onSwiper"
    @slideChange="onSlideChange"
  >
    <swiper-slide>Slide 1</swiper-slide>
    <swiper-slide>Slide 2</swiper-slide>
    <swiper-slide>Slide 3</swiper-slide>
    ...
  </swiper>
  </div>
  <div id="portfolio">
    <div class="header">포트폴리오</div>

    <div class="list">
      <div class="item" @click="movePage"></div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import { Swiper, SwiperSlide } from 'swiper/vue';
import aos from "aos";
// Import Swiper styles
import 'swiper/css';

export default {
  name: 'HomeView',
  components: {
      Swiper,
      SwiperSlide,
    },
    setup() {
      const onSwiper = (swiper) => {
        console.log(swiper);
      };
      const onSlideChange = () => {
        console.log('slide change');
      };
      return {
        onSwiper,
        onSlideChange,
      };
    },
    mounted() {
      aos.init();
    },
    methods: {
      movePage(path) {
        this.$router.push(path);
      }
    }
}
</script>



<style lang="less">

.list {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 10px;

  .item {
    width: 100%;
    background-position: center center;
    background-size: cover;
    aspect-ratio: 1/1;
    border
  }
}
</style>
