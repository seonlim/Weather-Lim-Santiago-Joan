<script setup>
import HelloWorld from './components/HelloWorld.vue'
import NavComponent from './components/NavBar.vue'
import FooterComponent from './components/Footer.vue'
import Header from './components/Header.vue'
import CurrentData from './services/Current.vue'
import ForecastVue from './components/Forecast.vue'
import {ref} from 'vue'
const city = ref('');


function searchCity(cityReceived) {
  city.value=cityReceived;
}
</script>

<template>
    <Header @city="searchCity($event)"/>
    <NavComponent/>
  <FooterComponent/>
  <CurrentData :city="city"/>
  <section class="main">
  <ForecastVue/>
  <p>Other Components</p>
  </section>
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
