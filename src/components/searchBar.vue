<template>
  <div>searchbar {{ state.search }}</div>
</template>

<script>
import state from "../store.js";
export default {
  name: "searchBar",
  data() {
    return {
      state,
    };
  },
  methods: {},
};
</script>

<style lang="scss" scoped></style>
