<template>
  <div class="footer relative py-[80px]">
    <div class="container">
      <div class="flex justify-around">
        <ul class="flex flex-col gap-2 first">
          <li
            class="not-italic cursor-pointer font-normal text-2xl leading-7 text-white destinationInFooter"
          >
            Destinations
          </li>
          <li class="cursor-pointer">Uzbekistan</li>
          <li class="cursor-pointer">Kazakhstan</li>
          <li class="cursor-pointer">Kygrizistan</li>
          <li class="cursor-pointer">Tajikistan</li>
          <li class="cursor-pointer">Turkmenistan</li>
          <li
            class="cursor-pointer not-italic font-normal text-2xl leading-7 text-white destinationInFooter"
          >
            Tour Agency Blog
          </li>
        </ul>
        <ul class="lg:w-[200px] md:w-[200px] w-[200px]">
          <li
            class="not-italic font-normal text-2xl leading-7 text-white destinationInFooter"
          >
            Call us
          </li>
          <p class="not-italic font-normal text-base text-white mb-7">
            <a href="tel:+998 97 732 01 97">+998 97 732 01 97</a><br />
            <a href="tel: +998 94 181 01 97"> +998 94 181 01 97</a>
          </p>
          <li
            class="destinationInFooter not-italic font-normal text-2xl leading-7 text-white"
          >
            E-mail us
          </li>
          <p class="not-italic font-normal text-base leading-5 text-white mb-7">
            <a href="mailto: abc@example.com"> hello@samar@com </a>
          </p>
          <li
            class="destinationInFooter not-italic font-normal text-2xl leading-7 text-white"
          >
            Find Us
          </li>
          <p class="not-italic font-normal text-base text-white">
            50, st Ozod sharq, Samarkand, Uzbekistan
          </p>
        </ul>
        <div
          class="md:flex lg:flex hidden md:flex-col items-center justify-start gap-4"
        >
          <a href="/">
            <img src="../../assets/icons/logo.svg" alt="" />
          </a>
          <img src="../../assets/icons/footerSvg.svg" alt="" />
          <img src="../../assets/icons/petit.svg" alt="" />
          <div class="flex items-center gap-4">
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
          </div>
        </div>
        <button
          @click="up"
          class="absolute border rounded-full p-2 bottom-8 hover:border-[#949494] right-11"
        >
          <img
            class="rotate-90"
            src="../../assets/icons/ourServicesArrow.svg"
            alt=""
          />
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    up: function () {
      window.scrollTo({
        top: 0,
        behavior: "smooth",
      });
    },
  },
};
</script>

<style lang="scss" scoped>
.footer {
  background-image: url("../../assets/images/footerBg.png");
  ul {
    color: white;
    li:hover {
      color: rgb(170, 170, 170);
    }
  }
  .first {
    li {
      font-style: normal;
      font-weight: 700;
      font-size: 16px;
      line-height: 30px;
      color: #ffffff;
    }
  }
}
@media (max-width: 480px) {
  .footer {
    padding: 20px 0;
  }
  ul {
    li {
      font-size: 15px;
    }
  }
}
</style>
