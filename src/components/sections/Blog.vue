<template>
  <div class="blog">
    <main class="container">
      <h2 class="main-desc">Blog</h2>
      <div
        class="grid lg:grid-cols-12 md:grid-cols-12 grid-cols-12 lg:gap-9 md:gap-9"
      >
        <div
          class="lg:col-span-5 md:col-span-12 grid-cols-12 main-section-in-blog-page"
        >
          <img
            class="lg:w-full md:w-full w-[345px]"
            src="../../assets/images/blogMainImg.png"
            alt=""
          />
          <p
            class="not-italic font-medium text-2xl text-red-900 mt-[25px] mr-0"
          >
            Presentation of our blog.
          </p>
          <p
            class="not-italic font-normal text-xl text-gray-900 mt-5 lg:w-full md:w-full w-[355px]"
          >
            Contrary to popular belief, Lorem Ipsum is not simply random text.
            It has roots in a piece of classical Latin literature from 45 BC,
            making it over 2000 years old.
          </p>
        </div>
        <div
          class="lg:col-span-7 md:col-span-12 col-span-12 mt-8 h-[550px] blogOverFlowScrollElement overflow-y-scroll"
        >
          <div
            v-for="(card, index) in data"
            :key="index"
            class="card lg:flex md:flex block gap-[30px] mb-8 cursor-pointer"
          >
            <img
              class="lg:w-[300px] md:lg:w-[300px] w-[250px] lg:h-[225px] md:h-[225px] h-[145px] object-cover rounded-[20px]"
              :src="card.img"
              alt=""
            />
            <div>
              <p
                class="not-italic font-medium lg:text-xl md:lg:text-xl text-[20px] text-red-900 hover:text-red-500 mt-2"
              >
                {{ card.title }}
              </p>
              <p
                class="lg:mt-5 md:mt-5 mt-2 lg:w-full md:w-full w-[325px] not-italic font-normal lg:text-xl md:lg:text-xl text-[17px] text-gray-900 hover:text-gray-700"
              >
                {{ card.desc }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </main>
  </div>
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

<style>
@media (max-width: 1020px) {
  .main-section-in-blog-page {
    grid-column: span 12 / span 12;
  }
}
</style>
