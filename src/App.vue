<script setup>
import Header from './components/Header.vue'
import Main from './components/Main.vue'
import UpcomingTrips from './components/UpcomingTrips.vue'
import Mainv2 from './components/Mainv2.vue';
import DoneTrips from './components/DoneTrips.vue';
</script>

<template>
  <Mainv2 />
  <UpcomingTrips />
  <DoneTrips />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
