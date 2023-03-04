<script setup>
import { useStore } from "vuex";
import { useRouter } from "vue-router";
import { computed } from "vue";
import { auth } from "../services/firebase/index.js"

const store = useStore();
const router = useRouter();

auth.onAuthStateChanged((user) => {
  store.dispatch('fetchUser', user)
});

const user = computed(() => {
  return store.getters.user;
});

const signOut = async () => {
  await store.dispatch('logOut')
  router.push('/login')
};

</script>

<template>
  <div v-if="user.loggedIn">
    <p>Welcome, {{ user.data.displayName }}</p>
    <p>You are logged in!</p>
    <button @click.prevent="signOut">Log Out</button>
  </div>

  <div v-else class="alert alert-danger" role="alert">
    You are not logged in!
  </div>
</template>


<style>
</style>