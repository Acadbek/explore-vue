<template>
  <Carousel class="relative" ref="carousel" v-model="currentSlide">
    <Slide v-for="slide in slides" :key="slide.id">
      <div class="w-full">
        <img class="carousel w-full" :src="slide.image" alt="" />
      </div>
      <div class="main-title">
        <h1 class="not-italic font-medium text-center uppercase text-white">
          THE GREAT SILK ROAD
        </h1>
        <p
          class="not-italic font-normal text-2xl leading-7 text-center text-white"
        >
          Come to explore the mysterious lands of the East
        </p>
      </div>
    </Slide>
  </Carousel>

  <div
    class="flex items-center justify-between absolute w-full bottom-0 bg-[#6C6C6C] opacity-70 h-[50px] px-[80px]"
  >
    <button
      class="z-50 flex items-center justify-center bg-[#c9c9c9] opacity-90 rounded-full w-9 h-9"
      @click="prev"
    >
      <img src="../assets/icons/left.svg" alt="" />
    </button>
    <Pagination />
    <button
      class="z-50 flex items-center justify-center bg-[#c9c9c9] opacity-90 rounded-full w-9 h-9"
      @click="next"
    >
      <img src="../assets/icons/right.svg" alt="" />
    </button>
  </div>
</template>

<script>
import { defineComponent } from "vue";
import { Carousel, Slide, Pagination } from "vue3-carousel";

import "vue3-carousel/dist/carousel.css";

import slide1 from "../assets/images/bg.png";
import slide2 from "../assets/images/bg2.png";
import slide3 from "../assets/images/bg3.png";
import slide4 from "../assets/images/bg4.png";

export default defineComponent({
  components: {
    Carousel,
    Slide,
  },
  data: () => ({
    currentSlide: 0,
    slides: [
      {
        id: 1,
        image: slide1,
        title: "THE GREAT SILK ROAD",
        desc: "Come to explore the mysterious lands of the East",
      },
      {
        id: 1,
        image: slide2,
        title: "THE GREAT SILK ROAD",
        desc: "Come to explore the mysterious lands of the East",
      },
      {
        id: 1,
        image: slide3,
        title: "THE GREAT SILK ROAD",
        desc: "Come to explore the mysterious lands of the East",
      },
      {
        id: 1,
        image: slide4,
        title: "THE GREAT SILK ROAD",
        desc: "Come to explore the mysterious lands of the East",
      },
    ],
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
.carousel {
  height: 100vh;
  object-fit: cover;
}
.main-title {
  position: absolute;
  top: 50%;
  right: 50%;
  transform: translate(50%, -50%);
  z-index: 999999 !important;
}
.main-title h1 {
  font-size: 72px;
  font-family: "El Messiri", sans-serif;
  font-weight: 700 !important;
}
@media (max-width: 450px) {
  .main-title h1 {
    font-size: 40px;
  }
}
</style>
