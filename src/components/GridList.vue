<template>
  <section>
    <h2>{{ title }}</h2>
    <ul>
      <CardComponent v-for="card in items" :key="card.id" :item="card" />
    </ul>
  </section>
</template>

<script>
import CardComponent from "./CardComponent.vue";

export default {
  components: { CardComponent },
  name: "GridList",
  props: {
    items: Array,
    loader: Boolean,
    title: String,
  },
  data() {
    return {};
  },
  computed: {},
};
</script>

<style lang="scss"></style>
