<template>
  <header class="container-fluid d-flex mx-0 px-2 align-items-center justify-content-between">
    <img src="@/img/spotify-logo.png" alt="" />
      <!-- Ricerca per genere -->
      <label for="select-genre" class="mx-5">
        Cerca per genere:
        <select name="genre" id="select-genre">
          <option value="All" selected>All</option>
          <option
          v-for="genre in propGenresList"
          :value="genre"
          :key="genre"
          >
          {{genre}}
          </option>
        </select>
      </label>
  </header>
</template>

<script>

export default {
  name: 'HeaderPage',
  props: {
    propGenresList: Array,
  },
  components: {
  },
  data() {
    return {
      genreFilter: 'all',
    };
  },
  methods: {
    genreChange() {
      this.$emit('changedGenre', this.genreFilter);
    },
  },
};
</script>

<style lang="scss" scoped>
header {
  display: flex;
  height: 5rem;
  width: 100vw;
  background-color: rgb(46, 58, 70);
}
img {
  width: 4rem;
}
</style>
