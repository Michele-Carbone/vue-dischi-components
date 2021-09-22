<template>
  <main class="container">
    <section id="album-container">
      <div v-for="disc in filteredDiscs" :key="disc.title" class="card">
        <Card :disc="disc" />
      </div>
    </section>
  </main>
</template>

<script>
import Card from "@/components/Card.vue";

export default {
  name: "Collection",

  components: {
    Card,
  },
  props: ["filteredDiscs"],
};
</script>

<style scoped lang="scss">
@import "@/assets/scss/style.scss";

#album-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

#album-container .card {
  background-color: #2e3a46;
  margin: 15px;
  flex-basis: 200px;
  text-align: center;
  min-height: 350px;
}
</style>