<template>
  <div id="app">
    <Search_Navbar />
    <Collection_Album />
  </div>
</template>

<script>
import Search_Navbar from "@/components/Search_Navbar.vue";
import Collection_Album from "@/components/Collection_Album";

export default {
  name: "App",
  components: {
    Search_Navbar,
    Collection_Album,
  },
};
</script>

<style >
</style>
