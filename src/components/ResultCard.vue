<template>
  <v-card class="d-flex justify-space-between mb-6 mt-6"  max-width="1800px" flat>
    <weather-card v-for="i in weatherData" :key="i.dt" :cityName='name' :weather="i" ></weather-card>
  </v-card>
</template>

<script>
import WeatherCard from "./WeatherCard.vue";
  export default {
    name: 'ResultCard',
    components : {
      WeatherCard
    },
    props : ['weatherData' , 'name'],

    data: () => ({
    }),
  }
</script>
