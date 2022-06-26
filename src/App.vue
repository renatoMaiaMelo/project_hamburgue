<template>
  <Navbar :logo="img" :msgAlt="alt" />
  <router-view />
  <Footer />
</template>

<script>
import Footer from "./components/Footer.vue";
import Navbar from "./components/Navbar.vue";
export default {
  components: { Navbar, Footer },
  data() {
    return {
      img: "img/logo.png",
      alt: "logoHamburgue",
    };
  },
};
</script>
<style>
@import "@/assets/base.css";
</style>
