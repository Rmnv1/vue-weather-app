<template>
  <div id="app">
    <main class="content-container">

      <Search @queryCreate="fetchWeather" />

      <Weather v-if="typeof weather.name != 'undefined'" 
               v-bind:city="weather.name" 
               v-bind:country="weather.sys.country"
               v-bind:temp="weather.main.temp"
               v-bind:main="weather.weather[0].main"
               />
      
    </main>
  </div>
</template>

<script>
import Search from './components/Search.vue'
import Weather from './components/Weather.vue'

export default {
  name: 'App',
  components: {
    Search, Weather
  },
  data() {
    return {
      api_key: 'd5f93e8e1dda3c6af51577abf48e8440',
      api_url: 'https://api.openweathermap.org/data/2.5/',
      query: '',
      weather: {}
    }
  },
  methods: {
    fetchWeather(textQuery) {
      fetch(`${this.api_url}weather?q=${textQuery.query}&units=metric&APPID=${this.api_key}`)
        .then(response => {
          if (!response.ok){
            throw Error(`is not ok: ` + resp.status);
          }
          return response.json();
        })
        .then(this.setResults)
        .catch((err) => {
          alert('City not found')
          console.log('City not found')
        })
    },
    setResults (results) {
      this.weather = results
    }
  }
}
</script>

<style lang="scss">

// Vars
$mainColor: #58BBC9;
$appWidth: 335px;

// Font
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@300&display=swap');

// Animations
@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body{
  font-family: 'Open Sans', sans-serif;
  background-color: $mainColor;
}
#app {
  width: 100%;
  min-height: 100vh;
}
.content-container{
  width: 100%;
  max-width: $appWidth;
  margin: 0 auto;
  padding: 0 5px;
}

</style>
