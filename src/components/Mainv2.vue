<template>
  <div class="mainv2">
    <Header />
    <Main />
  </div>
</template>

<script setup>
import Main from "./Main.vue";
import Header from "./Header.vue";
</script>

<style lang="scss" scoped>
.mainv2 {
  background-image: url("public/mountains-1-crop.jpg");
  background-repeat: no-repeat;
  background-position: top;
  background-size: cover;
  height: 100vh;
}
</style>