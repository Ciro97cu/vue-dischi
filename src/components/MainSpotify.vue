<template>
  <main>
    <div class="container-sm">
      <div v-if="arraySong.length > 0" class="row justify-content-between">
        <SongCard
          class="col-sm-2"
          v-for="(song, index) in arraySong"
          :key="index"
          :song="song"
        />
      </div>
    </div>
  </main>
</template>

<script>
import SongCard from "@/components/SongCard.vue";
import axios from "axios";

export default {
  name: "MainSpotify",
  data() {
    return {
      arraySong: [],
    };
  },
  components: {
    SongCard,
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((response) => {
        this.arraySong = response.data.response;
        // console.log(this.arraySong);
      });
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/style/variables";

main {
  background-color: $color-blue;
  height: calc(100vh - 46px);
  display: flex;
  align-items: center;
}
</style>