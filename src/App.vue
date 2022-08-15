<template>
  <div class="flex flex-col">
    <Header />
    <Destinations />
    <Tours />
    <AboutUs />
    <Blog />
    <Footer />
  </div>
</template>

<script>
import Header from "./layouts/header/header.vue";
import Footer from "./layouts/footer/footer.vue";
import Destinations from "./components/sections/Destinations.vue";
import Tours from "./components/sections/Tours.vue";
import AboutUs from "./components/sections/About-us.vue";
import Blog from "./components/sections/Blog.vue";
export default {
  name: "App",
  components: { Header, Footer, Destinations, Tours, AboutUs, Blog },
};
</script>

<style></style>
