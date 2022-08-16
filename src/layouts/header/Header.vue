<template>
  <div>
    <header class="header absolute top-0 z-50 w-full">
      <div class="container">
        <nav class="nav flex items-center justify-between h-[110px]">
          <div>
            <a href="/">
              <img src="../../assets/icons/logo.svg" alt="" />
            </a>
          </div>
          <ul class="flex gap-10">
            <li
              v-for="(link, index) in menus"
              :key="index"
              @click="choose(link.id)"
              :class="{ active: link.id === activeID }"
              class="not-italic font-normal text-2xl leading-7 cursor-pointer hover:text-[#d8d7d7] text-white"
            >
              {{ link.title }}
            </li>
          </ul>
          <div class="social-icons flex items-center gap-5">
            <img
              class="cursor-pointer"
              src="../../assets/icons/facebook.svg"
              alt=""
            />
            <img
              class="cursor-pointer"
              src="../../assets/icons/insta.svg"
              alt=""
            />
            <img
              class="cursor-pointer"
              src="../../assets/icons/youtube.svg"
              alt=""
            />
            <img
              class="cursor-pointer"
              src="../../assets/icons/linkedin.svg"
              alt=""
            />
            <div class="ml-4">
              <select class="cursor-pointer outline-none px-1 bg-transparent">
                <option value="uzb">🇬🇧</option>
                <option value="uzb">🇷🇺</option>
              </select>
            </div>
          </div>
        </nav>
      </div>
    </header>
    <section>
      <Carousel />
    </section>
  </div>
</template>

<script>
import "./header.css";
import Carousel from "../../components/carousel-component.vue";
export default {
  data() {
    return {
      menus: [
        { id: 1, title: "Silk Road Destinations" },
        { id: 2, title: "Tours" },
        { id: 3, title: "Agency" },
        { id: 4, title: "Blog" },
        { id: 5, title: "Contact" },
      ],
      activeID: false,
    };
  },
  methods: {
    choose: function (id) {
      this.activeID = id;
    },
  },
  components: { Carousel },
};
</script>

<style>
.active {
  color: #0073df !important;
}
</style>
