<script setup>
import WeatherDisplay from './components/WeatherDisplay.vue'
import WeatherForm from './components/WeatherForm.vue'

const handleSubmitSearch = (searchString) => {
  console.log('here is the searchString', searchString)
}
</script>

<template>
  <WeatherForm @submitSearch="handleSubmitSearch" />
  <WeatherDisplay />
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
