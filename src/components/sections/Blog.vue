<template>
  <main class="container">
    <h2 class="main-desc">Blog</h2>
    <div class="grid grid-cols-12 gap-10">
      <div class="lg:col-span-5 md:col-span-5 col-span-12">
        <img src="../../assets/images/blogMainImg.png" alt="" />
        <p class="not-italic font-medium text-2xl text-red-900 mt-[25px] mr-0">
          Presentation of our blog.
        </p>
        <p class="not-italic font-normal text-xl text-gray-900 mt-5">
          Contrary to popular belief, Lorem Ipsum is not simply random text. It
          has roots in a piece of classical Latin literature from 45 BC, making
          it over 2000 years old.
        </p>
      </div>
      <div
        class="lg:col-span-7 md:col-span-7 col-span-12 h-[550px] blogOverFlowScrollElement overflow-y-scroll"
      >
        <div
          v-for="(card, index) in data"
          :key="index"
          class="card flex gap-[30px] mb-8"
        >
          <img
            class="w-[300px] h-[225px] object-cover rounded-[20px]"
            :src="card.img"
            alt=""
          />
          <div>
            <p class="not-italic font-medium text-xl text-red-900">
              {{ card.title }}
            </p>
            <p class="mt-5 not-italic font-normal text-xl text-gray-900">
              {{ card.desc }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import img from "../../assets/images/aboutUsCarouselImg.png";
export default {
  data() {
    return {
      data: [
        {
          id: 1,
          img: img,
          title: "Where does it come from?",
          desc: "Contrary to popular belief, Lorem Ipsum is not simply random text. It has roots in a piece of classical Latin literature from 45 BC, making it over 2000 years old.",
        },
        {
          id: 2,
          img: img,
          title: "Where does it come from?",
          desc: "Contrary to popular belief, Lorem Ipsum is not simply random text. It has roots in a piece of classical Latin literature from 45 BC, making it over 2000 years old.",
        },
        {
          id: 3,
          img: img,
          title: "Where does it come from?",
          desc: "Contrary to popular belief, Lorem Ipsum is not simply random text. It has roots in a piece of classical Latin literature from 45 BC, making it over 2000 years old.",
        },
        {
          id: 4,
          img: img,
          title: "Where does it come from?",
          desc: "Contrary to popular belief, Lorem Ipsum is not simply random text. It has roots in a piece of classical Latin literature from 45 BC, making it over 2000 years old.",
        },
      ],
    };
  },
};
</script>