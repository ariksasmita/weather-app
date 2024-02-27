<script setup>
import { defineProps, computed } from 'vue'
const props = defineProps({
  city: String,
  state: String,
  degree: Number,
  weather: String,
  icon: String,
})

const iconUrl = computed(() => {
  if (!props.icon) return ''
  return `https://openweathermap.org/img/wn/${props.icon}@2x.png`
})

</script>

<template>
  <div class="header">
    <div class="title">
      <h1 class="city-name">{{ city }}, {{ state }}</h1>
      <h3 class="date">Sun, 31 Dec</h3>
    </div>
    <div class="weather">
      <div class="icon">
        {{ weather }}
        <img :src="iconUrl" :alt="weather">
      </div>
    </div>
    <div class="temperature">
      <h2 class="degree">{{ degree }} <span>&#176;C</span></h2>
    </div>
  </div>
</template>