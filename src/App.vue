<template>
  <div id="app">
    <HeaderPage :propGenresList="genresList"
    @changedGenre="genreChange"/>
    <MainPage @genresReady="getGenresList"
    :propGenresFilter="genreFilter"/>
  </div>
</template>

<script>
import HeaderPage from './components/HeaderPage.vue';
import MainPage from './components/MainPage.vue';

export default {
  name: 'App',
  components: {
    HeaderPage,
    MainPage,
  },
  data() {
    return {
      genresList: [],
      genreFilter: 'all',
    };
  },
  methods: {
    getGenresList(genresList) {
      this.genresList = genresList;
    },
    genreChange(genreFilter) {
      console.log(genreFilter);
      this.genreFilter = genreFilter;
    },
  },
};
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";
</style>
