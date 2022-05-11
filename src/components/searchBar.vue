<template>
  <div>searchbar {{ mysearch }}</div>
</template>

<script>
import state from "../store.js";
export default {
  name: "searchBar",
  data() {
    return {};
  },
  computed: {
    mysearch() {
      return state.search;
    },
  },
  methods: {},
};
</script>

<style lang="scss" scoped></style>
