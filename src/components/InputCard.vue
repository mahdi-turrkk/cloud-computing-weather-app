<template>
  <v-container>
    <v-card class="d-flex justify-center mb-6 mt-6" flat>
      <h2>Welcome</h2>
    </v-card>
    <v-card class="d-flex justify-center mb-6 mt-6" flat>
      <h4>please enter your city name</h4>
      </v-card>
    <v-card class="d-flex justify-center mb-6 mt-6" flat >
      <v-text-field style="max-width : 300px" placeholder="City Name" v-model="cityName"></v-text-field>
    </v-card>
    <v-card class="d-flex justify-center mb-6 mt-6" flat >
      <v-btn @click="getWeather" dark color="#ffbe0b">Get Weather</v-btn>
    </v-card>
  </v-container>
</template>

<script>
  export default {
    name: 'InputCard',
    components : {
    },

    data: () => ({
      cityName : ""
    }),
    methods : {
      getWeather(){
        this.$emit('getWeather', this.cityName)
      }
    }
  }
</script>
