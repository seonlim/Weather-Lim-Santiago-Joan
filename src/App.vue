<script setup>
import HelloWorld from './components/HelloWorld.vue'
import NavComponent from './components/NavBar.vue'
import FooterComponent from './components/Footer.vue'
import Header from './components/Header.vue'
import CurrentData from './services/Current.vue'
import ForecastVue from './components/Forecast.vue'
import Informations from './components/Informations.vue'
import TypeSelector from './components/TypeSelector.vue'
import { ref } from 'vue'
const infoWeather = ref({})
function sendData(weatherD){
infoWeather.value=weatherD;
}
const city = ref('');
const temp = ref('');
const hour = ref('');
function searchCity(cityReceived) {
  city.value=cityReceived;
}
function tempHandler(temperature) {
temp.value=temperature;
}
function sendHour(hourR){
hour.value=hourR;
}
</script>

<template>
    <Header @city="searchCity($event)"/>
    <NavComponent/>
    <section class="front">
  <TypeSelector @tempType="tempHandler"/>
  <CurrentData @dataWeather="sendData" @hourDay="sendHour" :temp="temp"  :city="city"/>
    </section>
  <section class="main">
  <ForecastVue :hour="hour" :temp="temp" :city="city"/>
      <Informations :infoWeather="infoWeather"/>
  </section>
  <FooterComponent/>

</template>

<style scoped>
#app{
  align-items: center;
  justify-content: center;
}
.main{
  display: flex;
  justify-content:center;
  padding-bottom: 4vh;
}
</style>
