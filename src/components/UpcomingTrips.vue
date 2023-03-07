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
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 320"><path fill="#029bc5" fill-opacity="1" d="M0,64L17.1,96C34.3,128,69,192,103,192C137.1,192,171,128,206,128C240,128,274,192,309,186.7C342.9,181,377,107,411,101.3C445.7,96,480,160,514,186.7C548.6,213,583,203,617,186.7C651.4,171,686,149,720,133.3C754.3,117,789,107,823,138.7C857.1,171,891,245,926,261.3C960,277,994,235,1029,229.3C1062.9,224,1097,256,1131,250.7C1165.7,245,1200,203,1234,202.7C1268.6,203,1303,245,1337,261.3C1371.4,277,1406,267,1423,261.3L1440,256L1440,0L1422.9,0C1405.7,0,1371,0,1337,0C1302.9,0,1269,0,1234,0C1200,0,1166,0,1131,0C1097.1,0,1063,0,1029,0C994.3,0,960,0,926,0C891.4,0,857,0,823,0C788.6,0,754,0,720,0C685.7,0,651,0,617,0C582.9,0,549,0,514,0C480,0,446,0,411,0C377.1,0,343,0,309,0C274.3,0,240,0,206,0C171.4,0,137,0,103,0C68.6,0,34,0,17,0L0,0Z"></path></svg>
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
    background-color: #1abc9c;
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