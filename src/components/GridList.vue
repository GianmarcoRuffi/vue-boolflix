<template>
  <section>
    <h2>{{ title }}</h2>
    <ul>
      <li v-for="item in items" :key="item.id">
        Poster:
        <img
          :src="'https://image.tmdb.org/t/p/w342/' + item.poster_path"
          :alt="item.title"
        />
        <br />
        id: {{ item.id }}<br />
        Titolo Originale:
        {{ item.original_title ? item.original_title : item.original_name
        }}<br />
        Titolo: {{ item.title ? item.title : item.name }}<br />
        Lingua: {{ item.original_language }}<br />

        <img :src="getFlag(item.original_language)" />

        Voto: {{ item.vote_average }}<br />
      </li>
    </ul>
  </section>
</template>

<script>
//import {state, actions} from '../store.js'
export default {
  name: "GridList",
  props: {
    items: Array,
    loader: Boolean,
    title: String,
  }, //['items','loader'],
  data() {
    return {};
  },
  computed: {
    // mysearch(){
    //     return state.search
    // }
  },
  methods: {
    getFlag(flag) {
      switch (flag) {
        case "en":
          return "https://flagcdn.com/16x12/uk.png";
        case "it":
          return "https://flagcdn.com/16x12/it.png";
        case "fr":
          return "https://flagcdn.com/16x12/fr.png";
        case "es":
          return "https://flagcdn.com/16x12/es.png";
        case "de":
          return "https://flagcdn.com/16x12/de.png";
        case "ru":
          return "https://flagcdn.com/16x12/ru.png";
        default:
          return flag;
      }
    },
  },
};
</script>

<style lang="scss"></style>
