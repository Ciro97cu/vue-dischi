<template>
  <div id="app">
    <HeaderSpotify />
    <MainSpotify />
  </div>
</template>

<script>
import HeaderSpotify from "./components/HeaderSpotify.vue";
import MainSpotify from "./components/MainSpotify.vue";

// import axios from 'axios';

export default {
  name: "App",
  components: {
    HeaderSpotify,
    MainSpotify,
  },
};
</script>

<style lang="scss">
@import "@/assets/style/imports";
#app {
  font-family: "Montserrat", sans-serif;
}
</style>
