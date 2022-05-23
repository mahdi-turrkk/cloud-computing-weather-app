<template>
  <v-card
    class="mx-auto"
    max-width="400"
  >
    <v-list-item two-line>
      <v-list-item-content>
        <v-list-item-title class="text-h5">
          {{ cityName }}
        </v-list-item-title>
        <v-list-item-subtitle>{{weather.dt_txt}},{{weather.weather[0].main}}</v-list-item-subtitle>
      </v-list-item-content>
    </v-list-item>

    <v-card-text>
      <v-row align="center">
        <v-col
          class="text-h6"
          cols="6"
        >
          {{weather.main.feels_like}}&deg;C
        </v-col>
      </v-row>
    </v-card-text>

    <v-list-item>
      <v-list-item-icon>
        <v-icon>mdi-send</v-icon>
      </v-list-item-icon>
      <v-list-item-subtitle>{{ weather.wind.speed }} km/h</v-list-item-subtitle>
    </v-list-item>
  </v-card>
</template>

<script>
  export default {
    name: 'WeatherCard',

    props : ['cityName' , 'weather'],

    data: () => ({
    }),
  }
</script>
