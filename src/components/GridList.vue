<template>
  <section>
    Sono GridList
    <button @click="leggi">clicca</button>
    {{ mysearch }}
  </section>
</template>

<script>
import state from "../store.js";
export default {
  name: "GridList",
  data() {
    return {};
  },
  computed: {
    mysearch() {
      return state.search;
    },
  },
  methods: {
    leggi() {
      state.search = "pippo";
    },
  },
};
</script>

<style lang="scss" scoped></style>
