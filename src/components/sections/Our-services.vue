<template>
  <div class="ourServices pt-[130px] mt-24">
    <div class="container">
      <dir class="grid grid-cols-12">
        <div class="col-span-8">
          <h2
            class="not-italic font-normal text-white text-[100px] leading-[90px]"
          >
            What They Says About Our Services
          </h2>
        </div>
        <div class="btns gap-[20px] flex items-start col-span-4">
          <button
            @click="prev"
            class="border-white p-4 border rounded-lg active:bg-white"
          >
            <img src="../../assets/icons/ourServicesArrow.svg" alt="" />
          </button>
          <button
            @click="next"
            class="border-white p-4 border rounded-lg active:bg-white"
          >
            <img
              class="rotate-180"
              src="../../assets/icons/ourServicesArrow.svg"
              alt=""
            />
          </button>
        </div>
      </dir>
      <div>
        <Carousel
          ref="carousel"
          :settings="settings"
          :breakpoints="breakpoints"
          class="mt-[50px]"
        >
          <Slide v-for="slide in data" :key="slide.id">
            <div
              class="carousel__item mr-[10px] bg-[#DFDFDF] w-[464px] pb-[20px] rounded-2xl pt-[44px] px-[27px]"
            >
              <p class="text-justify">{{ slide.review }}</p>
              <div
                class="flex items-center gap-3 justify-start mt-8 py-2 px-4 rounded-xl bg-[#D6EBE4]"
              >
                <img :src="slide.img" alt="" />
                <div class="text-start">
                  <p
                    class="not-italic font-bold text-xl leading-7 text-gray-900"
                  >
                    {{ slide.name }}
                  </p>
                  <p
                    class="not-italic font-normal text-base leading-7 text-gray-900 opacity-70"
                  >
                    {{ slide.country }}
                  </p>
                </div>
              </div>
            </div>
          </Slide>
        </Carousel>
      </div>
    </div>
  </div>
</template>

<script>
import { defineComponent } from "vue";
import { Carousel, Slide } from "vue3-carousel";

import "vue3-carousel/dist/carousel.css";

import img from "../../assets/images/Image.png";

export default defineComponent({
  components: {
    Carousel,
    Slide,
  },
  data: () => ({
    data: [
      {
        id: 1,
        review:
          "Samarkand Explore organized our tailor-made trip in Uzbekistan with a professionalism. Our trip allowed us to explore the historical cities of Silk Road and also to enjoy fully our family trip in this young country. We highly recommend this local young travel agency to the future travelers. ",
        img: img,
        name: "Michel M",
        country: "Canada",
      },
      {
        id: 2,
        review:
          "Samarkand Explore organized our tailor-made trip in Uzbekistan with a professionalism. Our trip allowed us to explore the historical cities of Silk Road and also to enjoy fully our family trip in this young country. We highly recommend this local young travel agency to the future travelers. ",
        img: img,
        name: "Michel M",
        country: "Canada",
      },
      {
        id: 3,
        review:
          "Samarkand Explore organized our tailor-made trip in Uzbekistan with a professionalism. Our trip allowed us to explore the historical cities of Silk Road and also to enjoy fully our family trip in this young country. We highly recommend this local young travel agency to the future travelers. ",
        img: img,
        name: "Michel M",
        country: "Canada",
      },
      {
        id: 4,
        review:
          "Samarkand Explore organized our tailor-made trip in Uzbekistan with a professionalism. Our trip allowed us to explore the historical cities of Silk Road and also to enjoy fully our family trip in this young country. We highly recommend this local young travel agency to the future travelers. ",
        img: img,
        name: "Michel M",
        country: "Canada",
      },
      {
        id: 5,
        review:
          "Samarkand Explore organized our tailor-made trip in Uzbekistan with a professionalism. Our trip allowed us to explore the historical cities of Silk Road and also to enjoy fully our family trip in this young country. We highly recommend this local young travel agency to the future travelers. ",
        img: img,
        name: "Michel M",
        country: "Canada",
      },
    ],
    settings: {
      itemsToShow: 3,
      snapAlign: "center",
    },
    breakpoints: {
      700: {
        itemsToShow: 2,
        snapAlign: "center",
      },
      1024: {
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

<style lang="scss" scoped>
.carousel {
  height: 450px;
}
.ourServices {
  background-image: url("../../assets/images/Review.png");
  width: 100%;
}
.carousel__track {
  display: flex;
  gap: 10px;
}
</style>
