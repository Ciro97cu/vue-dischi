<template>
  <select
    name="genre"
    id="genre"
    @change="$emit('search', displayGenre($event))"
  >
    <option value="All">All</option>
    <option value="Rock">Rock</option>
    <option value="Pop">Pop</option>
    <option value="Jazz">Jazz</option>
    <option value="Metal">Metal</option>
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