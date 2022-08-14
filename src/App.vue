<template>
  <Header />
  <Destinations />
  <Footer />
</template>

<script>
import Header from "./layouts/header/header.vue";
import Footer from "./layouts/footer/footer.vue";
import Destinations from "./components/sections/Destinations.vue";
export default {
  name: "App",
  components: { Header, Footer, Destinations },
};
</script>

<style></style>
