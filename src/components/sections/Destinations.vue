<template>
  <div class="destination py-[100px]">
    <div class="container">
      <div class="flex destination-top justify-between items-center">
        <p
          class="not-italic font-normal text-center md:text-[117px] text-[45px] text uppercase text-[#31C0FF]"
        >
          Destinations
        </p>
        <div
          class="flex destination-buttons md:gap-6 gap-2 not-italic font-bold text-[12px] md:text-base leading-7 text-center uppercase text-black"
        >
          <button
            v-for="(item, index) in countries"
            @click="filter(item.id)"
            :class="{ active: item.id === activeID }"
            :key="index"
          >
            <p class="hover:text-[#1faae6]">
              {{ item.name }}
            </p>
          </button>
        </div>
      </div>
    </div>
    <Carousel
      class="carousel"
      ref="carousel"
      :settings="settings"
      :breakpoints="breakpoints"
    >
      <Slide v-for="slide in datas" :key="slide.id">
        <div class="carousel__item mr-[25px]">
          <img
            :style="{
              width: '355px',
              height: '470px',
              borderRadius: '48px',
            }"
            class="object-cover destination-image"
            :src="slide.img"
            alt=""
          />
          <div class="details">
            <p
              class="mt-[24px] not-italic font-normal text-base leading-7 text-center text-black"
            >
              {{ slide.desc }}
            </p>
            <button
              class="not-italic hover:text-[#1c50c0] hover:border-[#1c50c0] font-normal border-[#407BFF] border-2 py-4 px-8 rounded-full mt-5 text-base text-center uppercase text-[#407BFF]"
            >
              View more
            </button>
          </div>
        </div>
      </Slide>
    </Carousel>
  </div>
</template>

<script>
import { defineComponent } from "vue";
import { Carousel, Pagination, Slide } from "vue3-carousel";

import "vue3-carousel/dist/carousel.css";
import img1 from "../../assets/images/destination1.png";
import img2 from "../../assets/images/destination2.png";
import img3 from "../../assets/images/destination3.png";
import img4 from "../../assets/images/destination4.png";
import img5 from "../../assets/images/destination5.png";

export default defineComponent({
  components: {
    Carousel,
    Slide,
    Pagination,
  },
  data() {
    return {
      datas: [
        {
          id: 1,
          img: img1,
          name: "kyrgyzstan",
          desc: "The land of high mountains and grassy steppes is a destination for nature lovers.",
        },
        {
          id: 2,
          img: img2,
          name: "Uzbekistan",
          desc: "The land of high mountains and grassy steppes is a destination for nature lovers.",
        },
        {
          id: 3,
          img: img3,
          name: "Kazakhstan",
          desc: "The land of high mountains and grassy steppes is a destination for nature lovers.",
        },
        {
          id: 4,
          img: img4,
          name: "Tajikistan",
          desc: "The land of high mountains and grassy steppes is a destination for nature lovers.",
        },
        {
          id: 5,
          img: img5,
          name: "TURKMENISTAN",
          desc: "The land of high mountains and grassy steppes is a destination for nature lovers.",
        },
        {
          id: 6,
          img: img1,
          name: "Uzbekistan",
          desc: "The land of high mountains and grassy steppes is a destination for nature lovers.",
        },
        {
          id: 7,
          img: img2,
          name: "Kazakhstan",
          desc: "The land of high mountains and grassy steppes is a destination for nature lovers.",
        },
        {
          id: 8,
          img: img3,
          name: "Tajikistan",
          desc: "The land of high mountains and grassy steppes is a destination for nature lovers.",
        },
      ],
      settings: {
        itemsToShow: 3.95,
        wrapAround: true,
      },
      breakpoints: {
        // 700px and up
        700: {
          itemsToShow: 3.5,
          snapAlign: "center",
        },
        // 1024 and up
        1024: {
          itemsToShow: 4.5,
          snapAlign: "center",
        },
        1350: {
          itemsToShow: 4,
          snapAlign: "center",
        },
        1214: {
          itemsToShow: 4,
          snapAlign: "center",
        },
        1135: {
          itemsToShow: 4,
          snapAlign: "center",
        },
        1100: {
          itemsToShow: 3.5,
          snapAlign: "center",
        },
        1599: {
          itemsToShow: 4.5,
          snapAlign: "center",
        },
        1500: {
          itemsToShow: 4.5,
          snapAlign: "center",
        },
        1400: {
          itemsToShow: 4.4,
          snapAlign: "center",
        },
        1300: {
          itemsToShow: 4.5,
          snapAlign: "center",
        },
        1200: {
          itemsToShow: 4.2,
          snapAlign: "center",
        },
        950: {
          itemsToShow: 3.5,
          snapAlign: "center",
        },
        870: {
          itemsToShow: 3,
          snapAlign: "center",
        },
        770: {
          itemsToShow: 2.5,
          snapAlign: "center",
        },
        760: {
          itemsToShow: 2.5,
          snapAlign: "center",
        },
        750: {
          itemsToShow: 2.5,
          snapAlign: "center",
        },
        740: {
          itemsToShow: 2.5,
          snapAlign: "center",
        },
        730: {
          itemsToShow: 2.5,
          snapAlign: "center",
        },
        720: {
          itemsToShow: 2.5,
          snapAlign: "center",
        },
        710: {
          itemsToShow: 2.5,
          snapAlign: "center",
        },
        690: {
          itemsToShow: 2.5,
          snapAlign: "center",
        },
        375: {
          itemsToShow: 1.5,
          snapAlign: "center",
        },
      },
      countries: [
        { id: 1, name: "Uzbekistan" },
        { id: 2, name: "Kazakhstan" },
        { id: 3, name: "Kyrgyzstan" },
        { id: 4, name: "Turkmenistan" },
        { id: 5, name: "Tajikistan" },
      ],
      activeID: false,
    };
  },
  methods: {
    filter: function (id) {
      this.activeID = id;
      console.log(this.datas);
    },
    next() {
      this.$refs.carousel.next();
    },
    prev() {
      this.$refs.carousel.prev();
    },
  },
});
</script>

<style scoped>
.carousel__slide > .carousel__item {
  transform: scale(1);
  opacity: 0.5;
  transition: 0.5s;
}
.carousel__slide--visible > .carousel__item {
  opacity: 1;
  transform: rotateY(0);
}
.carousel__slide--next > .carousel__item {
  transform: scale(0.9) translate(-10px);
}
.carousel__slide--prev > .carousel__item {
  transform: scale(0.9) translate(10px);
}

.details {
  display: none;
}

.carousel__slide--active {
  margin-bottom: 200px;
}
.carousel__slide--active .details {
  display: block;
}
.carousel__track {
  display: flex !important;
  gap: 25px;
}
.carousel__slide .carousel__slide--active .carousel__slide--visible {
  width: 0 !important;
}
.text {
  font-family: "Bebas Neue", cursive;
}
.active {
  color: #2898ff;
}
@media (max-width: 1284px) {
  .destination-top {
    display: flex;
    flex-direction: column;
  }
  .destination-buttons {
    margin-bottom: 28px;
  }
}
@media (max-width: 450px) {
  .destination-image {
    height: 255px !important;
  }
  .carousel__slide--active {
    margin-bottom: 0;
  }
  .details p {
    margin: 5px 0;
    font-size: 15px;
  }
  .details button {
    margin: 5px 0;
    font-size: 15px;
    padding: 5px 10px;
  }
}
.destination {
  background-image: url("../../assets/images/destination-bg.png");
}
.carousel {
  max-height: 803px;
}
</style>
