<script setup>
import { db } from '../services/firebase/index'
import { collection, getDocs, query } from "firebase/firestore"
import { ref, onMounted } from 'vue'

const travels = ref([])

onMounted( async () => {
  const querySnapshot = await getDocs(collection(db, "travels"))
  let firebase_Travels = []
  querySnapshot.forEach((doc) => {
    console.log(doc.id, " => ", doc.data())
    const travel = {
      id: doc.id,
      title: doc.data().title,
      location: doc.data().location,
      description: doc.data().description,
      banner_image: doc.data().banner_image
    }
    firebase_Travels.push(travel)
  })
  travels.value = firebase_Travels
})
</script>

<template>
  <section class="upcoming-trips">
    <div class="container">
      <h3>Proximos viajes</h3>
      <p>
        A continuación podrás ver algunos de los viajes que estamos planeando y organizando.
      </p>

      <div class="upcards-grid container">
        <div class="upcard" v-for="trip in travels" :key="trip.id">
          <img :src="trip.banner_image" alt="Banner image">
          <div class="upcard-info">
            <h1>{{ trip.title }}</h1>
            <span>📍{{ trip.location }}</span>
            <p>{{ trip.description }}</p>
            <a id="to_trip_button" href="#">Me interesa</a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import "../styles/variables";
h1,h2,h3,p, span {
  margin: 0;
}
.upcoming-trips {
  background-color: $gray;
  padding: 8rem 0;
  h3 {
    font-family: $montserrat;
    text-align: center;
    color: $sea-deep;
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
        #to_trip_button {
          border-radius: 10px;
          text-decoration: none;
          color: $white;
          background-color: $deep-blue;
          padding: 1.5rem 1rem;
          font-size: 1rem;
          transition: .5s;
          font-family: $normal-text;
          &:hover {
            font-size: 1.05rem;
            padding: 1rem 1.5rem;
            transition: .5s;
          }
        }
      }
      
    }
  }
}
</style>