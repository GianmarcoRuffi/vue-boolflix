<template>
  <div id="app">
    <header><h1 class="display-6">Boolflix</h1></header>
    <searchBar />

    <main><grid-list /></main>
  </div>
</template>

<script>
import GridList from "./components/GridList.vue";
import searchBar from "./components/searchBar.vue";
export default {
  name: "App",
  components: { searchBar, GridList },
};
</script>

<style lang="scss">
#app {
  @import "./styles/general.scss";
}
</style>
