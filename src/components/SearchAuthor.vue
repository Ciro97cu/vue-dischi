<template>
  <select
    name="author"
    id="author"
    @change="$emit('searchAuthor', displayAuthor($event))"
  >
    <option v-for="(item, index) in autore" :key="index" :value="item">
      {{ item }}
    </option>
  </select>
</template>

<script>
export default {
  name: "SearchAuthor",
  methods: {
    displayAuthor: function (event) {
      return event.target.value;
    },
  },
  props: {
    autore: Array,
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