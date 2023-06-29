<script setup>
import HelloWorld from './components/HelloWorld.vue'
import NavComponent from './components/NavBar.vue'
import FooterComponent from './components/Footer.vue'
import Header from './components/Header.vue'
import CurrentData from './services/Current.vue'
import ForecastVue from './components/Forecast.vue'
import Informations from './components/Informations.vue'
import { ref } from 'vue'
const infoWeather = ref({})
function sendData(weatherD){
infoWeather.value=weatherD;
console.log('app',infoWeather.value);
}
</script>

<template>
    <Header/>
    <NavComponent/>
    <CurrentData @dataWeather="sendData"/>
    <section class="main">
      <ForecastVue/>
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
}
</style>
