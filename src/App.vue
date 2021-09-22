<template>
  <div id="app">
    <Search :genres="genres" @genreSelector="selectedFilter" />
    <Load v-if="isLoading" />
    <Collection v-else :filteredDiscs="filteredDiscs" />
  </div>
</template>

<script>
import axios from "axios";
import Search from "@/components/Search.vue";
import Load from "@/components/Load.vue";
import Collection from "@/components/Collection";

export default {
  name: "App",
  components: {
    Search,
    Collection,
    Load,
  },
  data() {
    return {
      discs: [],
      genreFilter: "All",
      isLoading: true,
    };
  },
  computed: {
    genres() {
      const genres = [];
      this.discs.forEach((disc) => {
        if (!genres.includes(disc.genre)) genres.push(disc.genre);
      });
      return genres;
    },
    filteredDiscs() {
      let orderDiscs = [...this.discs];
      orderDiscs.sort((a, b) => a.year - b.year);
      if (this.genreFilter === "All") return orderDiscs;
      return orderDiscs.filter((disc) => disc.genre === this.genreFilter);
    },
  },
  created() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((res) => {
        this.discs = res.data.response;
        this.isLoading = false;
      });
  },
  methods: {
    selectedFilter(filter) {
      this.genreFilter = filter;
    },
  },
};
</script>

<style scoped lang="scss">
@import "assets/scss/style.scss";
</style>
