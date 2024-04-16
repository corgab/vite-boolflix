<template>
  <SearchBar/>
  <MoviesSection/>
  <FilmSection/>
</template>

<script>
  import SearchBar from "./components/SearchBar.vue";
  import MoviesSection from "./components/MoviesSection.vue"
  import FilmSection from "./components/FilmSection.vue"
  export default {
    components: {
      SearchBar,
      MoviesSection,
      FilmSection

    }
  }
</script>

<style lang="scss" scoped>

</style>