<template>
  <Header />
  <div class="h-screen"></div>
  <Footer />
</template>

<script>
import Header from "./layouts/header/header.vue";
import Footer from "./layouts/footer/footer.vue";
export default {
  name: "App",
  components: { Header, Footer },
};
</script>

<style></style>
