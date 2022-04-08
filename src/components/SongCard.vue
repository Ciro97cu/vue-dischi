<template>
  <div class="text-white song_card text-center p-3">
    <img :src="song.poster" :alt="song.title" class="w-100" />
    <h4>{{ song.title }}</h4>
    <p>{{ song.author }}</p>
    <p>{{ song.year }}</p>
  </div>
</template>

<script>
export default {
  name: "SongCard",
  props: {
    song: Object,
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/style/variables";

.song_card {
  background-color: $color-light-blue;
  display: flex;
  flex-direction: column;
  align-items: center;
  row-gap: 10px;
}
</style>