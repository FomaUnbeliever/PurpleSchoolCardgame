<script setup>
import { ref } from 'vue'
import CitySelect from './components/CitySelect.vue'
import Stat from './components/Stat.vue'

let savedCity = ref('Moscow')
let data =  ref({
  humidity: 90,
});



async function getCity(city) {
  savedCity.value = city;
  data.value.humidity = "20";
}
</script>

<template>
  <main class="main">
    {{ savedCity }}
    <Stat v-bind="data"></Stat>
    <Stat label="Влажность" :stat="data.humidity +'%'"/>
    <Stat label="Осадки" stat="0%"></Stat>
    <CitySelect @select-city="getCity" />
  </main>
</template>

<style scoped>
.main {
    background: var(--color-bg-main);
    padding: 60px 50px;
    border-radius: 25px;
}
</style>