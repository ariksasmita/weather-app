<script setup>
import { Cloud } from '@iconoir/vue'

const props = defineProps({
  city: String,
  state: String,
  degree: Number,
  weather: String,
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
        <Cloud
          color="lightblue"
          width="13rem"
          height="13rem"
          stroke-width="2"
         />
      </div>
    </div>
    <div class="temperature">
      <h2 class="degree">{{ degree }} <span>&#176;C</span></h2>
    </div>
  </div>
</template>