<template>
  <Carousel class="relative" ref="carousel" v-model="currentSlide">
    <Slide v-for="slide in slides" :key="slide.id">
      <div class="carousel__item w-full">
        <img class="carousel w-screen" :src="slide.image" alt="" />
      </div>
    </Slide>
    <template>
      <h1 class="absolute top-8 z-50 text-white">THE GREAT SILK ROAD</h1>
    </template>
  </Carousel>

  <div
    class="flex items-center justify-between absolute w-full bottom-0 bg-[#535353] opacity-70 h-[50px]"
  >
    <button
      class="z-50 flex items-center justify-center bg-[#a8a7a7] opacity-90 rounded-full w-9 h-9"
      @click="prev"
    >
      <img src="../assets/icons/left.svg" alt="" />
    </button>
    <button
      class="z-50 flex items-center justify-center bg-[#a8a7a7] opacity-90 rounded-full w-9 h-9"
      @click="next"
    >
      <img src="../assets/icons/right.svg" alt="" />
    </button>
  </div>
</template>

<script>
import { defineComponent } from "vue";
import { Carousel, Slide } from "vue3-carousel";

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
      { id: 1, image: slide1 },
      { id: 1, image: slide2 },
      { id: 1, image: slide3 },
      { id: 1, image: slide4 },
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
  height: calc(100vh - 0px);
  object-fit: cover;
}
</style>
