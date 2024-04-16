<template>
  <div class="bg-gray">
    <div class="container">
      <SearchBar/>
      <MoviesSection/>
      <FilmSection/>
    </div>
  </div>
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

<style lang="scss">
@use './assets/general.scss';

.flex {
  justify-content: space-between;
}

.bg-gray {
  background-color: rgb(211, 211, 211);
}

</style>