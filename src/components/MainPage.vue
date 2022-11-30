<template>
  <div class="main container-fluid d-flex flex-column align-items-center gap-5">
    <li v-for="genre in genArr" :key="genre">{{genre}}</li>
    <div class="container-fluid m-0 align-items-center d-flex d-wrap px-5">
      <ul class="row row-cols-5 g-5">
      </ul>
        <CardPage
        v-for="index in arrCDs"
        :key="index.title"
        :poster="index.poster"
        :title="index.title"
        :author="index.author"
        :year="index.year"
        />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import CardPage from './CardPage.vue';

export default {
  name: 'MainPage',
  components: {
    CardPage,
  },
  data() {
    return {
      cdAPI: 'https://flynn.boolean.careers/exercises/api/array/music',
      arrCDs: null,
    };
  },
  props: {
    genreFilter: String,
  },
  created() {
    axios.get(this.cdAPI)
      .then((axiosResponse) => {
        // console.log(axiosResponse);
        this.arrCDs = axiosResponse.data.response;
      });
  },
  computed: {
    genArr() {
      const arrGenres = [];
      if (this.arrCDs) { // se non è vuoto
        this.arrCDs.forEach((objDisk) => {
          if (!arrGenres.includes(objDisk.genre)) {
            arrGenres.push(objDisk.genre);
          }
        });
      }
      // console.log(arrGenres);
      return arrGenres;
    },
    arrDisksFiltered() {
      if (this.genreFilter === 'all') {
        return this.arrCDs;
      }
      return this.arrCDs.filter((objDisk) => objDisk.genre === this.genreFilter);
    },
  },
  watch: {
    arrGenres(newValue) {
      console.log(newValue); // PROBLEMA QUI, NON SI VEDE IL CONSOLE.LOG
      this.$emit('genresReady', newValue);
    },
  },
};
</script>

<style lang="scss" scoped>
.main{
  background-color: rgb(30, 45, 59);
  height: 95vh;
  position: absolute;
}
</style>
