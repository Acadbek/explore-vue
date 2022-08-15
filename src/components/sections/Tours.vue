<template>
  <div class="tours mt-[105px]">
    <div class="container">
      <div class="grid grid-cols-12 gap-6">
        <div class="col-span-4">
          <p class="main-desc mt-[270px]">Tours</p>
          <p
            class="not-italic font-normal w-[350px] text-base leading-6 text-black tracking-[0.48px] text-justify"
          >
            We invite you to come and explore the Silk Road in Uzbekistan such
            as magical Samarkand, beautiful Bukhara and mysterious Khiva, but
            also to feel and enjoy the hospitality of Uzbek people.
          </p>
        </div>
        <div class="col-span-8">
          <Carousel ref="carouselTours" :breakpoints="breakpoints">
            <Slide v-for="slide in 10" :key="slide">
              <div class="carousel__item flex gap-[40px]">
                <img
                  class="tours-image"
                  v-for="(item, index) in data"
                  :key="index"
                  :src="item.img"
                  alt=""
                />
              </div>
            </Slide>
            <template #addons>
              <div class="absolute top-[250px] left-[150px] flex gap-[400px]">
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
  </div>
</template>

<script>
import { defineComponent } from "vue";
import { Carousel, Slide } from "vue3-carousel";
import "vue3-carousel/dist/carousel.css";

import img1 from "../../assets/images/tours1.png";
import img2 from "../../assets/images/tours2.png";
import img3 from "../../assets/images/tours3.png";

export default defineComponent({
  components: {
    Carousel,
    Slide,
  },
  data() {
    return {
      data: [
        { id: 1, img: img1 },
        { id: 2, img: img2 },
        { id: 3, img: img3 },
      ],
      breakpoints: {
        // 700px and up
        700: {
          itemsToShow: 1,
        },
        // 1024 and up
        1024: {
          itemsToShow: 1,
        },
      },
    };
  },
  methods: {
    next() {
      this.$refs.carouselTours.next();
    },
    prev() {
      this.$refs.carouselTours.prev();
    },
  },
});
</script>

<style lang="scss" scoped>
.tours {
  background-image: url("../../assets/images/tours.png");
}
.carousel__prev--in-active,
.carousel__next--in-active {
  display: none;
}
.tours-image {
  width: 411px;
  height: 550px;
  object-fit: cover;
}
</style>
