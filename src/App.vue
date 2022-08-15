<template>
  <div class="flex flex-col">
    <!-- <Header /> -->
    <!-- <Destinations /> -->
    <!-- <Tours /> -->
    <!-- <AboutUs /> -->
    <!-- <Blog /> -->
    <!-- <OurServices /> -->
    <!-- <Partner /> -->
    <Footer />
  </div>
</template>

<script>
import Header from "./layouts/header/Header.vue";
import Footer from "./layouts/footer/Footer.vue";
import Destinations from "./components/sections/Destinations.vue";
import Tours from "./components/sections/Tours.vue";
import AboutUs from "./components/sections/About-us.vue";
import Blog from "./components/sections/Blog.vue";
import OurServices from "./components/sections/Our-services.vue";
import Partner from "./components/sections/Partner.vue";
export default {
  name: "App",
  components: {
    Header,
    Footer,
    Destinations,
    Tours,
    AboutUs,
    Blog,
    OurServices,
    Partner,
  },
};
</script>

<style></style>
