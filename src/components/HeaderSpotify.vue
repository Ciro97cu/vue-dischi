<template>
  <header class="container-fluid py-2">
    <div class="wrapper_logo">
      <img src="@/assets/img/spotify-svg.svg" alt="spotify-logo" />
    </div>
  </header>
</template>

<script>
export default {
  name: "HeaderSpotify",
};
</script>

<style lang="scss" scoped>
@import "@/assets/style/variables";
header {
  background-color: $color-light-blue;

  .wrapper_logo {
    width: 30px;

    img {
      width: 100%;
    }
  }
}
</style>