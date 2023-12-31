<script setup>
import { ref } from "vue";
import WeatherDisplay from "./components/WeatherDisplay.vue";
import WeatherForm from "./components/WeatherForm.vue";

const cityName = ref('')
const stateName = ref('')
const lat = ref('')
const lon = ref('')
const degree = ref(0)
const weather = ref('')

const handleSubmitSearch = async (searchString) => {
  // Get City Coordinate
  console.log("here is the searchString", searchString);
  const appid = "cdc06fab41045afce5f38fa0f21e9dee";
  try {
    const locationRes = await fetch(
      `http://api.openweathermap.org/geo/1.0/direct?q=${searchString}&limit=5&appid=${appid}`
    );
    const locationResJson = await locationRes.json();
    if (locationResJson.length > 0 && locationResJson[0]) {
      cityName.value = locationResJson[0].name
      stateName.value = locationResJson[0].state || locationResJson[0].country
      lat.value = locationResJson[0].lat
      lon.value = locationResJson[0].lon
    }
  } catch (e) {
    console.log(error);
  }
  if (!lat.value && !lon.value) return
  // Fetch weather data
  try {
    const weatherRes = await fetch(`https://api.openweathermap.org/data/2.5/weather?lat=${lat.value}&lon=${lon.value}&appid=${appid}&units=metric`)
    const weatherResJson = await weatherRes.json()
    degree.value = weatherResJson?.main?.temp
    weather.value = weatherResJson?.weather[0].main
  } catch (error) {
    console.log(error)
  }
};
</script>

<template>
  <WeatherForm @submitSearch="handleSubmitSearch" />
  <WeatherDisplay
    :city="cityName"
    :state="stateName"
    :degree="degree"
    :weather="weather"
  />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
