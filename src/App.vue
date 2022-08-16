<template>
  <div class="flex flex-col">
    <Header />
    <Main />
    <Footer />
  </div>
</template>

<script>
import Header from "./layouts/header/Header.vue";
import Footer from "./layouts/footer/Footer.vue";
import Main from "./layouts/main/Main.vue";

export default {
  name: "App",
  components: {
    Header,
    Footer,
    Main,
  },
};
</script>
