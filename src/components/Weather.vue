<template>
  <div class="weather">
    <div class="weather__top">
      <span class="weather__num">{{Math.round(this.temp)}}</span>
      <span class="weather__ico">°C</span>
    </div>
    <span class="weather__city-name">
      {{this.city}}, {{this.country}}
    </span>
    <div class="weather__icon-wrap">
      <img :src="getImgSrc(this.main)" alt="Weather icon" class="weather__icon">
      <span class="weather__icon-desc">
        {{this.main}}
      </span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Weather',
  props: {
    city: '',
    country: '',
    temp: '',
    feels: '',
    main: ''
  },
  methods: {
    getImgSrc(imgName) {
      switch(imgName.toLowerCase()) {
        case 'rain': return require(`./../assets/icons/rain.svg`)
        case 'drizzle': return require(`./../assets/icons/rain.svg`)
        case 'thunderstorm': return require(`./../assets/icons/thunderstorm.svg`)
        case 'snow': return require(`./../assets/icons/snow.svg`)
        default: return require(`./../assets/icons/clouds.svg`)
      }
    }
  }
}
</script>

<style scoped lang="scss">
.weather{
  width: 100%;
  height: 600px;
  margin-top: 30px;
  margin-bottom: 30px;
  border-radius: 5px;
  box-shadow: 0 19px 38px rgba(0,0,0,.3), 0 15px 12px rgba(0,0,0,.22);
  background-image: linear-gradient(rgba(0,0,0,.1),rgba(0,0,0,.1)),url('./../assets/images/day.jpg');
  background-size: cover;
  animation: .5s fadeIn;
}
.weather__top{
  display: flex;
  justify-content: center;
  align-items: center;
  padding-top: 40px;
}
.weather__num{
  font-size: 112px;
  font-weight: 600;
  color: #FFF;
  padding-left: 33px;
}
.weather__ico{
  font-size: 32px;
  font-weight: 600;
  color: #FFF;
  padding-bottom: 50px;
}
.weather__city-name{
  display: block;
  padding: 0 10px;
  text-align: center;
  font-size: 32px;
  color: #FFF;
  margin-top: 15px;
}

.weather__icon-wrap{
  width: 100%;
  max-width: 120px;
  display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 20px;
  text-align: center;
}
.weather__icon-desc{
  color: #FFF;
  font-weight: 600;
  font-size: 17px;
}

</style>
