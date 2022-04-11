<template>
  <main>
    <div class="container-sm">
      <div class="row justify-content-center">
        <div class="col-auto">
          <SearchGenre @search="searchbygenre" />
        </div>
      </div>

      <div
        v-if="arraySong.length > 0"
        class="row gy-4 justify-content-around pt-5"
      >
        <SongCard
          class="song_card"
          v-for="(song, index) in displaybygenre"
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
import SearchGenre from "@/components/SearchGenre.vue";
import axios from "axios";

export default {
  name: "MainSpotify",
  data() {
    return {
      arraySong: [],
      selectedGenre: "",
    };
  },
  components: {
    SongCard,
    LoaderSong,
    SearchGenre,
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((response) => {
        this.arraySong = response.data.response;
      });
  },
  methods: {
    searchbygenre: function (searchNameGenre) {
      this.selectedGenre = searchNameGenre;
    },
  },
  computed: {
    displaybygenre: function () {
      if (this.selectedGenre === "All") {
        return this.arraySong;
      }
      return this.arraySong.filter((element) => {
        return element.genre.includes(this.selectedGenre);
      });
    },
  },
};
</script>

<style lang="scss" scoped>
main {
  .container-sm {
    margin-top: 50px;
  }
  .song_card {
    width: 18%;
  }
}
</style>