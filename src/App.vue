<template>
  <v-app>
    <v-app-bar app color="#ffbe0b" dark height="50">
      <v-btn icon @click="back">
        <v-icon>mdi-arrow-left</v-icon>
      </v-btn>
      <v-spacer></v-spacer>
      <v-container>Weather App</v-container>
      <v-spacer></v-spacer>
    </v-app-bar>
    <v-main>
      <input-card v-if="isInput" @getWeather="getWeather"></input-card>
      <result-card v-if="isResult" :name='cityName' :weatherData='weatherData'></result-card>
    </v-main>
  </v-app>
</template>

<script>
import ResultCard from './components/ResultCard';
import InputCard from './components/InputCard';



export default {
  name: "App",

  components: {
    ResultCard,
    InputCard
  },

  data: () => ({
    cityName : "",
    isInput : true,
    isResult : false,
    weatherData : []
  }),
  methods : {
    getWeather(data){
      let lat = ''
      let lon = ''
      this.cityName = data
      fetch(`https://api.openweathermap.org/geo/1.0/direct?q=${data}&appid=2c15dcc8b030c2e671e32d29c5483615`)
      .then(response => {
        if (response.ok) {
          return response.json();
        } else {
          console.log("fuck")
        }
        }).then(coordination => {
          lat = coordination[0].lat
          lon = coordination[0].lon
          return lon
        }).then(d =>{
          fetch(`https://api.openweathermap.org/data/2.5/forecast?lat=${lat}&lon=${lon}&units=metric&cnt=50&appid=2c15dcc8b030c2e671e32d29c5483615`)
          .then(response => {
            console.log(d)
            if (response.ok) {
              return response.json();
            } else {
              console.log("fuck")
            }
            }).then(weather => {
              weather.list.splice(1 , 7)
              weather.list.splice(2 , 7)
              weather.list.splice(3 , 7)
              weather.list.splice(4 , 7)
              weather.list.splice(5 , 7)
              this.weatherData = weather.list
              console.log(weather.list)
            })
            this.back()
        })

        
    },
    back(){
      if(this.isInput == true){
        this.isInput = false
        this.isResult = true
      }    
      else{
        this.isInput = true
        this.isResult = false        
      }
    }
  }
};
</script>
