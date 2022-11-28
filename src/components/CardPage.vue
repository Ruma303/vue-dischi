<template>
  <div class="col">
   <div class="card content text-center " style="width: 18rem;">
    <img :src="poster" :alt="title" class="figure-img img-fluid p-4">
    <div class="card-body">
      <h2 class="song card-text">{{title}}</h2>
      <h4 class="author card-text">{{author}}</h4>
      <h5 class="year card-text">{{year}}</h5>
    </div>

   </div>
  </div>
</template>

<script>
export default {
  name: 'CardPage',
  props: {
    poster: String,
    title: String,
    author: String,
    year: Number,
  },
};
</script>

<style lang="scss" scoped>
.content{
  background-color: rgb(46, 58, 70);
  border: none;
  height: 450px;
}
.song{
font-size: 1.5rem;
}
.author{
font-size: 1.3rem;
font-weight: 400;
}
.year{
font-size: 1.2rem;
font-weight: 400;
}
</style>
