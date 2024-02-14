<template>
  <!-- Lägga in mina containar med interpolering av den informationen som ska visas -->
  <div class="container">
    <div class="inner-container">
      <h1>{{ name }}<span></span></h1>
      <h2>{{ temperature }}<span>&#176;</span></h2>
      <p>{{ weatherDescription }}</p>

      <!-- Lägger in informationen i mina variablar med bilder till rätt variabel -->

      <div v-if="showRainy" class="weather-condition">
        <img src="../assets/rain.png" alt="" />
      </div>
      <div v-if="showCloudy" class="weather-condition">
        <img src="../assets/cloudy.png" alt="" />
      </div>
      <div v-if="showStormy" class="weather-condition">
        <img src="../assets/storm.png" alt="" />
      </div>
      <div v-if="showSnowy" class="weather-condition">
        <img src="../assets/snow.png" alt="" />
      </div>
      <div v-if="showClear" class="weather-condition">
        <img src="../assets/sunny.png" alt="" />
      </div>

      <div class="input-container">
        <label for="latitude">Latitude</label>
        <input type="text" name="latitude" v-model="latitude" />
      </div>
      <div class="input-container">
        <label for="longitude">Longitude</label>
        <input type="text" name="longitude" v-model="longitude" />
      </div>
      <button @click="getWeatherData">Get Data</button>
    </div>
  </div>
</template>

<script setup>
import { onMounted } from 'vue'
import { ref } from 'vue'
import axios from 'axios'

const weatherDescription = ref('')
const showRainy = ref(false)
const showStormy = ref(false)
const showCloudy = ref(false)
const showSnowy = ref(false)
const showClear = ref(false)
const temperature = ref('')
const name = ref('')
const latitude = ref('59.334591')
const longitude = ref('18.063240')

/* Gör en GET med axios för att ta fram ovan information från min API  */

const getWeatherData = () => {
  axios
    .get(
      `https://api.openweathermap.org/data/2.5/weather?lat=${latitude.value}&lon=${longitude.value}&appid=5277f4c48a6d4d9b147a121e0ef2c66a&units=metric`
    )
    .then((response) => {
      console.log(response.data)
      const mainDescription = response.data.weather[0].main
      const descriptionString = response.data.weather[0].description
      weatherDescription.value =
        descriptionString.charAt(0).toUpperCase() + descriptionString.slice(1)
      temperature.value = response.data.main.temp
      name.value = response.data.name

      /* Detta gör jag för att få fram rätt bild vid rätt väder. */

      switch (true) {
        case mainDescription === 'Clouds':
          showCloudy.value = true
          showStormy.value = false
          showRainy.value = false
          showSnowy.value = false
          showClear.value = false
          break
        case mainDescription === 'Storm':
          showCloudy.value = false
          showStormy.value = true
          showRainy.value = false
          showSnowy.value = false
          showClear.value = false
          break
        case mainDescription === 'Rain':
          showCloudy.value = false
          showStormy.value = false
          showRainy.value = true
          showSnowy.value = false
          showClear.value = false
          break
        case mainDescription === 'Snow':
          showCloudy.value = false
          showStormy.value = false
          showRainy.value = false
          showSnowy.value = true
          showClear.value = false
          break
        case mainDescription === 'Clear':
          showCloudy.value = false
          showStormy.value = false
          showRainy.value = false
          showSnowy.value = false
          showClear.value = true
          break
        default:
      }
    })
    .catch((error) => {
      console.log(error)
    })
}
onMounted(getWeatherData)
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
}

.inner-container {
  width: 90%;
  max-width: 600px;
  background-color: #f0f0f0;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h2 {
  font-size: 2rem;
  margin-bottom: 10px;
}

p {
  font-size: 1.2rem;
  margin-bottom: 20px;
}

.weather-condition {
  margin-bottom: 10px;
}

.input-container {
  margin-bottom: 10px;
}

label {
  display: block;
  margin-bottom: 5px;
}

input[type='text'] {
  width: 100%;
  padding: 10px;
  font-size: 1rem;
  border-radius: 5px;
  border: 1px solid #ccc;
}

button {
  background-color: #1a614d;
  color: #fff;
  padding: 10px 20px;
  font-size: 1rem;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #1e4976;
}
</style>
