<script setup>
import { db } from '../services/firebase/index'
import { collection, getDocs } from "firebase/firestore"
import { ref, onMounted } from 'vue'

const travels = ref([])
onMounted( async () => {
  const querySnapshot = await getDocs(collection(db, "travels"))
  let firebase_Travels = []
  querySnapshot.forEach((doc) => {
    if (doc.data().status === 'done') {
      const travel = {
        id: doc.id,
        title: doc.data().title,
        location: doc.data().location,
        description: doc.data().description,
        banner_image: doc.data().banner_image,
        status: doc.data().status
      }
      firebase_Travels.push(travel)
    }
  })
  travels.value = firebase_Travels
})

const props = defineProps({
  status: String,
});
</script>

<template>
  <section class="upcoming-trips">
    <div class="container">
      <h3>Viajes que hemos hecho</h3>
      <p>
        A continuación podrás ver algunos de los viajes que hemos realizado en el pasado.
      </p>

      <div class="upcards-grid container">
        <div class="upcard" v-for="trip in travels" :key="trip.id">
          <div>
            <img :src="trip.banner_image" alt="Banner image" />
            <div class="upcard-info">
              <h1>{{ trip.title }}</h1>
              <span>📍{{ trip.location }}</span>
              <p>{{ trip.description }}</p>
              <a id="to_trip_button" href="#">Ver</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import "../styles/variables";
.upcoming-trips {
  background-color: $green;
  h3 {
    color: $white;
  }
  p {
    color: $white;
  }
  .upcard {
    background-color: $gray;
    p {
      color: $sea-deep;
    }
  }
}
</style>