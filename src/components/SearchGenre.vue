<template>
  <select
    name="genre"
    id="genre"
    @change="$emit('search', displayGenre($event))"
  >
    <option v-for="(item, index) in genere" :key="index" :value="item">
      {{ item }}
    </option>
  </select>
</template>

<script>
export default {
  name: "SearchGenre",
  methods: {
    displayGenre: function (event) {
      return event.target.value;
    },
  },
  props: {
    genere: Array,
  },
};
</script>

<style lang="scss" scoped>
select {
  background-color: #2e3a46;
  border: 1px solid white;
  border-radius: 5px;
  padding: 5px;
  color: white;
  cursor: pointer;
}
</style>