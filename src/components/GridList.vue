<template>
  <section>
    <ul>
      <li v-for="movie in movies" :key="movie.id">
        id:
        {{ movie.id }}
        <br />
        titolo originale:
        {{ movie.original_title }}
        titolo:
        {{ movie.title }}
        lingua:
        {{ movie.original_language }}
        <img src="require('./assets/images/'+item.original.language+ '.jpg')" />
        voto:
        {{ movie.vote_Average }}
      </li>
    </ul>
  </section>
</template>

<script>
import state from "../store.js";
export default {
  name: "GridList",
  props: { items: Array, loader: Boolean },
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
