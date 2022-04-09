<template>
  <main>
    <div class="container-sm">
      <div v-if="arraySong.length > 0" class="row gy-4 justify-content-between">
        <SongCard
          class="song_card"
          v-for="(song, index) in arraySong"
          :key="index"
          :song="song"
        />
      </div>
      <div v-else class="row justify-content-center">
        <LoaderSong />
      </div>
    </div>
  </main>
</template>

<script>
import SongCard from "@/components/SongCard.vue";
import LoaderSong from "@/components/LoaderSong.vue";
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
    LoaderSong,
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((response) => {
        this.arraySong = response.data.response;
      });
  },
};
</script>

<style lang="scss" scoped>
main {
  .container-sm {
    margin-top: 100px;
  }
  .song_card {
    width: 18%;
  }
}
</style>