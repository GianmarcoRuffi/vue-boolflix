<template>
  <div>
    <input
      type="text"
      v-model="search"
      @keyup.enter="$emit('performSearch', search)"
    />
    <button @click="cerca">Cerca</button>
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

<style lang="scss"></style>
