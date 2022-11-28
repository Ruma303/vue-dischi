<template>
  <header class="container-fluid d-flex mx-0 px-2 align-items-center">
    <img src="@/img/spotify-logo.png" alt="">
  </header>
</template>

<script>
export default {
  name: 'HeaderPage',
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
