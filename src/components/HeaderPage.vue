<template>
  <header class="container-fluid d-flex mx-0 px-2 align-items-center justify-content-between">
    <img src="@/img/spotify-logo.png" alt="" />
    <form action="">
      <!-- DROPDOWN MENU PER GENERI -->
      <font-awesome-icon icon="fa-solid fa-chevron-right" />
      <!-- INPUT RICERCA -->

    </form>
  </header>
</template>

<script>
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';

export default {
  name: 'HeaderPage',
  components: { FontAwesomeIcon },
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
