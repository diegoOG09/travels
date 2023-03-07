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
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 320"><path fill="#f6d7b0" fill-opacity="1" d="M0,64L16,90.7C32,117,64,171,96,181.3C128,192,160,160,192,144C224,128,256,128,288,154.7C320,181,352,235,384,245.3C416,256,448,224,480,224C512,224,544,256,576,256C608,256,640,224,672,208C704,192,736,192,768,208C800,224,832,256,864,234.7C896,213,928,139,960,122.7C992,107,1024,149,1056,149.3C1088,149,1120,107,1152,85.3C1184,64,1216,64,1248,69.3C1280,75,1312,85,1344,101.3C1376,117,1408,139,1424,149.3L1440,160L1440,0L1424,0C1408,0,1376,0,1344,0C1312,0,1280,0,1248,0C1216,0,1184,0,1152,0C1120,0,1088,0,1056,0C1024,0,992,0,960,0C928,0,896,0,864,0C832,0,800,0,768,0C736,0,704,0,672,0C640,0,608,0,576,0C544,0,512,0,480,0C448,0,416,0,384,0C352,0,320,0,288,0C256,0,224,0,192,0C160,0,128,0,96,0C64,0,32,0,16,0L0,0Z"></path></svg>
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
  background-color: $blue;
  h3 {
    padding-top: 2rem;
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