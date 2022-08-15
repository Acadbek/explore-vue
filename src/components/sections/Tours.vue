<template>
  <div class="container">
    <div class="flex tours items-start gap-[100px]">
      <div class="max-w-[350px]">
        <p class="main-desc mt-[12rem]">Tours</p>
        <p
          class="not-italic font-normal text-base leading-6 text-black mt-[7px]"
        >
          We invite you to come and explore the Silk Road in Uzbekistan such as
          magical Samarkand, beautiful Bukhara and mysterious Khiva, but also to
          feel and enjoy the hospitality of Uzbek people.
        </p>
      </div>
      <div>
        <Carousel
          ref="carousel"
          :settings="settings"
          :breakpoints="breakpoints"
        >
          <Slide v-for="slide in data" :key="slide">
            <div class="carousel__item">
              <img
                :style="{ height: '575px', objectFit: 'cover' }"
                :src="slide.img"
                alt=""
              />
            </div>
          </Slide>

          <template #addons>
            <div class="flex justify-around absolute top-[270px] w-full">
              <button @click="prev">
                <img
                  class="rotate-180"
                  src="../../assets/icons/toursNext.svg"
                  alt=""
                />
              </button>
              <button @click="next">
                <img src="../../assets/icons/toursNext.svg" alt="" />
              </button>
            </div>
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
import { Carousel, Slide } from "vue3-carousel";

import "vue3-carousel/dist/carousel.css";

export default defineComponent({
  components: {
    Carousel,
    Slide,
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
      300: {
        itemsToShow: 1,
        snapAlign: "center",
      },
      // 700px and up
      375: {
        itemsToShow: 1,
        snapAlign: "center",
      },
      599: {
        itemsToShow: 2.5,
        snapAlign: "center",
      },
      700: {
        itemsToShow: 3,
        snapAlign: "center",
      },
      // 1024 and up
      1024: {
        itemsToShow: 3,
        snapAlign: "start",
      },
      1290: {
        itemsToShow: 3,
        snapAlign: "start",
      },
    },
  }),
  methods: {
    next() {
      this.$refs.carousel.next();
    },
    prev() {
      this.$refs.carousel.prev();
    },
  },
});
</script>

<style>
.carousel__prev--in-active,
.carousel__next--in-active {
  display: none;
}
.tours {
  margin-top: 190px;
}
@media (max-width: 978px) {
  .tours {
    display: flex;
    flex-direction: column;
  }
  .main-desc {
    margin: 0;
  }
  .tours {
    margin: 0;
  }
}
</style>
