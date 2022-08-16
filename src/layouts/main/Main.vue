<template>
  <Destinations />
  <Tours />
  <AboutUs />
  <Blog />
  <OurServices />
  <Partner />
</template>

<script>
import Destinations from "../../components/sections/Destinations.vue";
import Tours from "../../components/sections/Tours.vue";
import AboutUs from "../../components/sections/About-us.vue";
import Blog from "../../components/sections/Blog.vue";
import OurServices from "../../components/sections/Our-services.vue";
import Partner from "../../components/sections/Partner.vue";
export default {
  name: "App",
  components: {
    Destinations,
    Tours,
    AboutUs,
    Blog,
    OurServices,
    Partner,
  },
};
</script>
