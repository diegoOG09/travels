<script setup>
import { db } from '../services/firebase/index'
import { collection, getDocs } from "firebase/firestore"
import { ref, onMounted } from 'vue'

const travels = ref([])

onMounted( async () => {
  const querySnapshot = await getDocs(collection(db, "travels"))
  let firebase_Travels = []
  querySnapshot.forEach((doc) => {
    if(doc.data().status === 'upcoming') {
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
</script>

<template>
  <section class="upcoming-trips">
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 320"><path fill="#009bc0" fill-opacity="1" d="M0,96L48,122.7C96,149,192,203,288,197.3C384,192,480,128,576,128C672,128,768,192,864,224C960,256,1056,256,1152,240C1248,224,1344,192,1392,176L1440,160L1440,0L1392,0C1344,0,1248,0,1152,0C1056,0,960,0,864,0C768,0,672,0,576,0C480,0,384,0,288,0C192,0,96,0,48,0L0,0Z"></path></svg>
    <div class="container">
      <h3>Proximos viajes</h3>
      <p>
        A continuación podrás ver algunos de los viajes que estamos planeando y organizando.
      </p>
      <div class="upcards-grid container">
        <div class="upcard" v-for="trip in travels" :key="trip.id">
          <div>
            <img :src="trip.banner_image" alt="Banner image">
            <div class="upcard-info">
              <h1>{{ trip.title }}</h1>
              <span>📍{{ trip.location }}</span>
              <p>{{ trip.description }}</p>
              <a class="to_trip_button" href="#">Me interesa</a>
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

<style lang="scss">
@import "../styles/variables";
.view_more_btn {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 4rem;
  #view_more_btn {
    background-color: $green;
  }
}
.upcoming-trips {
  background-color: $gray;
  padding-bottom: 10rem;
  h1,h2,h3,p, span {
    margin: 0;
  }
  h3 {
    font-family: $poppins;
    text-align: center;
    color: $sea-deep;
    margin-top: -5rem;
    margin-bottom: 2rem;
    font-size: 2.8rem;
  }
  p {
    text-align: center;
    font-family: $normal-text;
    font-size: 1.5rem;
    color: $sea-deep;
    margin-bottom: 4rem;
  }

  .to_trip_button {
    border-radius: 10px;
    text-decoration: none;
    color: $white;
    background-color: $blue;
    padding: 1rem 1.5rem;
    font-size: 1rem;
    transition: .5s;
    font-family: $normal-text;
    &:hover {
      font-size: 1.05rem;
      padding: .5rem 1.5rem;
      transition: .5s;
    }
  }

  .upcards-grid {
    display: flex;
    gap: 2rem;
    align-items: center;
    justify-content: center;
    .upcard {
      // box-shadow: rgba(0, 0, 0, 0.15) 2.4px 2.4px 3.2px;
      box-shadow: rgba(0, 0, 0, 0.08) 0px 4px 12px;
      border-radius: 10px;
      width: 20rem;
      height: 35rem;
      img {
        border-radius: 10px 10px 0 0;
        width: 20rem;
        height: 10rem;
      }
      .upcard-info {
        padding: 1rem;
        h1 {
          color: $sea-deep;
          font-family: $normal-text;
          font-size: 2rem;
        }
        span {
          color: #bfbfbf;
          font-size: 1rem;
          font-family: $normal-text;
          i {
            margin-right: .5rem;
            font-size: .8rem;
          }
        }
        p {
          margin-top: 1.5rem;
          font-size: 1rem;
          text-align: left;
          margin-bottom: 2.5rem;
        }
        
      }
    }
  }
}
</style>