<template>
  <div class="mainv2">
    <Header />
    <Main />
    <img id="background-img" src="/mountains-1-crop.jpg" alt="">
  </div>
</template>

<script setup>
import Main from "./Main.vue";
import Header from "./Header.vue";
</script>

<style lang="scss" scoped>
.mainv2 {
  margin-bottom: 7.2rem;
  #background-img {
    width: 100%;
    height: 100vh;
    z-index: -1;
    position: absolute;
    top: 0;
    filter: brightness(.75);
  }
}
</style>