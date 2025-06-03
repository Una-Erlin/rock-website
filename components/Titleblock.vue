<template>
  <div class="opacity-80 animate-fade animate-once animate-delay-[100ms]">
    <div class="text-2xl font-bold rubik-dirt-font">
      {{ settings.site_title }}
    </div>
    <div class="text-sm opacity-80">
      {{ settings.site_subtitle }}
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const settings = ref({});
const { data, error } = await useFetch('/_data/settings.json');

if (data.value) {
  settings.value = data.value;
} else if (error.value) {
  console.error('Error loading settings:', error.value);
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Rubik+Dirt&display=swap');

.rubik-dirt-font {
  font-family: 'Rubik Dirt', cursive, sans-serif;
}
</style>
