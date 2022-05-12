<template>
  <section>
    <!-- <h2>{{ title }}</h2> -->
    <div class="row d-flex wrap justify-content-center">
      <CardComponent v-for="card in items" :key="card.id" :item="card" />
    </div>
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

<style lang="scss">
section {
  background-color: grey;
  padding: 30px;
}
</style>
