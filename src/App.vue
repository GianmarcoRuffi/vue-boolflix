<template>
  <div id="app">
    <header><h1 class="display-6">Boolflix</h1></header>
    <searchBar @performSearch="search" />

    <main>
      <button @click="getMovies">Carica</button>

      <grid-list :items />
    </main>
  </div>
</template>

<script>
import GridList from "./components/GridList.vue";
import searchBar from "./components/searchBar.vue";
import axios from "axios";
export default {
  name: "App",
  components: { searchBar, GridList },
  data() {
    return {
      apiKey: "3b5d854d511c7b62449930d0a3312305",
      apiPath: "https://api.themoviedb.org/3/search/",
      movies: [],
    };
  },
  methods: {
    getMovies() {},
      search(text){
        const queryParams = {
          params: {
            api_key: this.apiKey,
            query: encodeURIComponent(text)
          },
        };
      }
      this.getMovies(queryParams),
        axios.get(this.apiPath + "movie", queryParams).then((res) => {
          // console.log(res);
          this.movies = res.data.results;
        });
    ,
  },
};
</script>

<style lang="scss">
#app {
  @import "./styles/general.scss";
}
</style>
