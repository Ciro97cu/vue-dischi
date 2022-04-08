<template>
  <div id="app">
    <HeaderSpotify />
    <MainSpotify />
  </div>
</template>

<script>
import HeaderSpotify from "./components/HeaderSpotify.vue";
import MainSpotify from "./components/MainSpotify.vue";

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
@import "@/assets/style/resets";

#app {
  font-family: "Montserrat", sans-serif;
}
</style>