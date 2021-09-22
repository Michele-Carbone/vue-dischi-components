<template>
  <div class="card">
    <img :src="disc.poster" :alt="disc.title" />
    <h2 class="title">{{ disc.title }}</h2>
    <address class="author">{{ disc.author }}</address>
    <time :datetime="disc.year" class="year">{{ disc.year }}</time>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: ["disc"],
};
</script>

<style scoped lang="scss">
@import "@/assets/scss/style.scss";

.card img {
  width: 100%;
  height: auto;
}

.card .title {
  color: #fff;
  margin: 15px 0;
  text-transform: uppercase;
}
.card .author,
.card .year {
  color: #808080;
  font-size: 21px;
}
.card .year {
  font-size: 16px;
}
</style>