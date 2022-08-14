<template>
  <div>
    <header class="header bg-blue-700">
      <div class="container">
        <nav class="nav flex items-center justify-between h-[110px]">
          <div>
            <img src="../../assets/icons/logo.svg" alt="" />
          </div>
          <ul class="flex gap-10">
            <li
              v-for="(link, index) in menus"
              :key="index"
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
              <select class="cursor-pointer" name="" id="">
                <option value="uzb">UZB</option>
              </select>
            </div>
          </div>
        </nav>
      </div>
    </header>
  </div>
</template>

<script>
import "./header.css";
export default {
  data() {
    return {
      menus: [
        { id: 1, title: "Silk Road Destinations" },
        { id: 1, title: "Tours" },
        { id: 1, title: "Agency" },
        { id: 1, title: "Blog" },
        { id: 1, title: "Contact" },
      ],
    };
  },
};
</script>
