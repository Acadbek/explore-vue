<template>
  <div class="flex flex-col">
    <Header />
    <Destinations />
    <Tours />
    <Footer />
  </div>
</template>

<script>
import Header from "./layouts/header/header.vue";
import Footer from "./layouts/footer/footer.vue";
import Destinations from "./components/sections/Destinations.vue";
import Tours from "./components/sections/Tours.vue";
export default {
  name: "App",
  components: { Header, Footer, Destinations, Tours },
};
</script>

<style></style>
