<template>
  <header>
    <div class="container">
      <img src="@/assets/images/logo.png" />
      <select
        @change="$emit('genreSelector', selectedFilter)"
        v-model="selectedFilter"
        name="genre-select"
        id="genre-select"
      >
        <option selected value="All">All</option>
        <option v-for="genre in genres" :key="genre" :value="genre">
          {{ genre }}
        </option>
      </select>
    </div>
  </header>
</template>

<script>
export default {
  name: "Search",
  props: ["genres"],
  data() {
    return {
      selectedFilter: "All",
    };
  },
};
</script>

<style lang="scss">
@import "@/assets/scss/style.scss";
/* Header */

header {
  background-color: #2e3a46;
  height: 70px;
  padding: 10px;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
}

header img {
  height: 50px;
}

header .container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 10px;
}
</style>