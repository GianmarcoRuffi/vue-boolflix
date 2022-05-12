<template>
  <div>
    <header class="d-flex">
      <div class="row d-flex">
        <div class="col-6">
          <h1>Boolflix</h1>
        </div>
        <div class="col-6">
          <input
            type="text"
            v-model="search"
            @keyup.enter="$emit('performSearch', search)"
          />
          <button @click="cerca">Cerca</button>
        </div>
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
  height: 100px;
  .row {
    display: flex;
    width: 100vh;

    .col-6 {
      display: flex;
      justify-content: center;
      align-content: center;
      width: 50%;
      height: 40px;
    }
  }
}

h1 {
  color: red;
}
</style>
