<template>
  <div class="main container-fluid m-0 align-items-center d-flex d-wrap px-5">
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
  margin-top: 5vh;
}
</style>
