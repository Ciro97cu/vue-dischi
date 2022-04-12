<template>
  <main>
    <div class="container-sm">
      <div class="row justify-content-center">
        <div class="col-auto">
          <p class="d-inline-block pe-2 text-white">Selezione per Genere</p>
          <SearchGenre @search="searchbygenre" :genere="arrayGenre" />
        </div>
        <div class="col-auto">
          <p class="d-inline-block pe-2 text-white">Selezione per Autore</p>
          <SearchAuthor @searchAuthor="searchbyauthor" :autore="arrayAuthor" />
        </div>
      </div>

      <div
        v-if="arraySong.length > 0"
        class="row gy-4 justify-content-around pt-5"
      >
        <SongCard
          class="song_card"
          v-for="(song, index) in displaybyfilters"
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
import SearchAuthor from "@/components/SearchAuthor.vue";
import axios from "axios";

export default {
  name: "MainSpotify",
  data() {
    return {
      arraySong: [],
      arrayGenre: [],
      arrayAuthor: [],
      selectedGenre: "All",
      selectedAuthor: "All",
    };
  },
  components: {
    SongCard,
    LoaderSong,
    SearchGenre,
    SearchAuthor,
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((response) => {
        this.arraySong = response.data.response;

        this.arraySong.filter((item) => {
          if (!this.arrayGenre.includes(item.genre)) {
            this.arrayGenre.push(item.genre);
          }
        });
        this.arrayGenre.unshift("All");

        this.arraySong.filter((item) => {
          if (!this.arrayAuthor.includes(item.author)) {
            this.arrayAuthor.push(item.author);
          }
        });
        this.arrayAuthor.unshift("All");
      });
  },
  methods: {
    searchbygenre: function (searchNameGenre) {
      this.selectedGenre = searchNameGenre;
    },
    searchbyauthor: function (searchNameAuthor) {
      this.selectedAuthor = searchNameAuthor;
      console.log(this.selectedAuthor);
    },
  },
  computed: {
    displaybyfilters: function () {
      const filter =
        this.selectedGenre === "All"
          ? this.arraySong
          : this.arraySong.filter((item) => item.genre === this.selectedGenre);
      if (this.selectedAuthor === "All") {
        return filter;
      }
      return filter.filter((item) => item.author === this.selectedAuthor);
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