<template>
  <div class="main container-fluid d-flex flex-column align-items-center gap-5">
    <SearchBar class="mt-5"/>
    <div class="container-fluid m-0 align-items-center d-flex d-wrap px-5">
      <ul v-if="arrCDs"
      class="row row-cols-5 g-5">
        <CardPage
        v-for="index in arrCDs"
        :key="index.title"
        :poster="index.poster"
        :title="index.title"
        :author="index.author"
        :year="index.year"
        />
      </ul>
      <div v-else>
        Loading...
        </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import CardPage from './CardPage.vue';
import SearchBar from './SearchBar.vue';

export default {
  name: 'MainPage',
  components: {
    CardPage,
    SearchBar,
  },
  data() {
    return {
      arrCDs: null,
      cdAPI: 'https://flynn.boolean.careers/exercises/api/array/music',
    };
  },
  created() {
    axios.get(this.cdAPI)
      .then((axiosResponse) => {
        console.log(axiosResponse);
        this.arrCDs = axiosResponse.data.response;
      });
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
