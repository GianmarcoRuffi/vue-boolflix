<template>
  <div>
    <header class="d-flex row">
      <div class="d-flex col-6 align-items-center">
        <h1 class="px-4">Boolflix</h1>
      </div>
      <div
        class="d-flex col-6 justify-content-center align-items-center justify-content-right"
      >
        <input
          type="text"
          v-model="search"
          @keyup.enter="$emit('performSearch', search)"
        />
        <button @click="cerca">Cerca</button>
      </div>
    </header>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  data() {
    return {
      search: "",
    };
  },
  computed: {},
  methods: {
    cerca() {
      this.$emit("performSearch", this.search);
      this.search = "";
    },
  },
};
</script>

<style lang="scss">
// @import "../styles/general.scss";
// @import "../styles/vars.scss";

header {
  display: flex;
  width: 100%;
  height: 80px;
  background-color: black;

  h1 {
    text-transform: uppercase;
    font-weight: bold;
    color: red;
  }
}
</style>
