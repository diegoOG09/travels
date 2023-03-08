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
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 320"><path fill="#f9d7b3" fill-opacity="1" d="M0,96L48,122.7C96,149,192,203,288,197.3C384,192,480,128,576,128C672,128,768,192,864,224C960,256,1056,256,1152,240C1248,224,1344,192,1392,176L1440,160L1440,0L1392,0C1344,0,1248,0,1152,0C1056,0,960,0,864,0C768,0,672,0,576,0C480,0,384,0,288,0C192,0,96,0,48,0L0,0Z"></path></svg>
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
              <a class="to_trip_button" href="#">Ver</a>
            </div>
          </div>
        </div>
      </div>
      <div class="view_more_btn">
        <a id="view_more_btn" class="to_trip_button" href="#">Ver más</a>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import "../styles/variables";
.upcoming-trips {
  background-color: $gray;
  h3 {
    padding-top: 2rem;
    color: $dark-text;
  }
  p {
    color: $dark-text;
  }
  .upcard {
    background-color: $gray;
    p {
      color: $sea-deep;
    }
  }
}
</style>