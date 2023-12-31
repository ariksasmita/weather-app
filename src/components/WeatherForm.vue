<script setup>
import { ref } from 'vue'
const emit = defineEmits(['submitSearch'])

const cityInput = ref('')
const emitToParent = () => {
  emit('submitSearch', cityInput.value)
}
</script>

<template>
  <div class="weather-form">
    <input v-model="cityInput" type="text" class="weather-input">
    <button @click="emitToParent">Search</button>
  </div>
</template>