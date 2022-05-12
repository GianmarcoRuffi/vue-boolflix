<template>
  <div id="app">
    <header>
      <h1 class="display-6">Boolflix</h1>
      <SearchBar @performSearch="search" />
    </header>
    <main>
      <GridList :items="movies" title="Movies" :loader="loading" />
      <GridList :items="series" title="Series" :loader="loadingSeries" />
    </main>
  </div>
</template>

<script>
import GridList from "./components/GridList.vue";
// import CardComponent from "./components/CardComponent.vue";
import SearchBar from "./components/SearchBar.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    SearchBar,
    GridList,
    // CardComponent,
  },
  data() {
    return {
      apiKey: "3b5d854d511c7b62449930d0a3312305",
      apiPath: "https://api.themoviedb.org/3/search/",
      movies: [],
      series: [],
      loading: false,
      loadingSeries: false,
    };
  },
  methods: {
    getMovies(queryParams) {
      axios
        .get(this.apiPath + "movie", queryParams)
        .then((res) => {
          //console.log(res.data.results)
          this.movies = res.data.results;
          this.loading = false;
        })
        .catch((error) => {
          console.log(error);
        });
    },
    getSeries(queryParams) {
      axios
        .get(this.apiPath + "tv", queryParams)
        .then((res) => {
          //console.log(res.data.results)
          this.series = res.data.results;
          this.loadingSeries = false;
        })
        .catch((error) => {
          console.log(error);
        });
    },

    search(text) {
      const queryParams = {
        params: {
          api_key: this.apiKey,
          query: text,
        },
      };
      this.loading = true;
      this.loadingSeries = true;
      this.getMovies(queryParams);
      this.getSeries(queryParams);
    },
  },
};
</script>

<style lang="scss">
@import "./styles/general.scss";
@import "./styles/vars.scss";
</style>
