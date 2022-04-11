<template>
  <main>
    <div class="container-sm">
      <div class="row justify-content-center">
        <div class="col-auto">
          <select
            name="genre"
            id="genre"
            v-model="selectedGenre"
            @change="displayGenre()"
          >
            <option value="All">All</option>
            <option value="Rock">Rock</option>
            <option value="Pop">Pop</option>
            <option value="Jazz">Jazz</option>
            <option value="Metal">Metal</option>
          </select>
        </div>
      </div>

      <div
        v-if="arraySong.length > 0"
        class="row gy-4 justify-content-around pt-5"
      >
        <SongCard
          class="song_card"
          v-for="(song, index) in displayGenre()"
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
      selectedGenre: "All",
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
  methods: {
    displayGenre() {
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

  select {
    background-color: #2e3a46;
    border: 1px solid white;
    border-radius: 5px;
    padding: 5px;
    color: white;
    cursor: pointer;
  }
}
</style>