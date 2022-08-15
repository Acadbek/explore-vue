<template>
  <div class="container">
    <div class="flex items-start justify-between">
      <div class="basis-2/5">text</div>
      <div>
        <Carousel :settings="settings" :breakpoints="breakpoints">
          <Slide v-for="slide in data" :key="slide">
            <div class="carousel__item mr-2">
              <img
                :style="{ height: '875px', width: '411px', objectFit: 'cover' }"
                :src="slide.img"
                alt=""
              />
            </div>
          </Slide>

          <template #addons>
            <Navigation />
          </template>
        </Carousel>
      </div>
    </div>
  </div>
</template>

<script>
import img1 from "../../assets/images/tours1.png";
import img2 from "../../assets/images/tours2.png";
import img3 from "../../assets/images/tours3.png";
import { defineComponent } from "vue";
import { Carousel, Navigation, Slide } from "vue3-carousel";

import "vue3-carousel/dist/carousel.css";

export default defineComponent({
  components: {
    Carousel,
    Slide,
    Navigation,
  },
  data: () => ({
    data: [
      { id: 1, img: img1 },
      { id: 2, img: img2 },
      { id: 3, img: img3 },
      { id: 1, img: img1 },
      { id: 2, img: img2 },
      { id: 3, img: img3 },
    ],
    // carousel settings
    settings: {
      itemsToShow: 3.5,
      snapAlign: "center",
    },
    // breakpoints are mobile first
    // any settings not specified will fallback to the carousel settings
    breakpoints: {
      // 700px and up
      700: {
        itemsToShow: 1,
        snapAlign: "center",
      },
      // 1024 and up
      1024: {
        itemsToShow: 3,
        snapAlign: "start",
      },
    },
  }),
});
</script>

<style>
/* .carousel__prev--in-active,
.carousel__next--in-active {
  display: none;
} */
</style>
