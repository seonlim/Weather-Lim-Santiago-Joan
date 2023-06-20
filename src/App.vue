<script setup>
import HelloWorld from './components/HelloWorld.vue'
import NavComponent from './components/NavBar.vue'
import FooterComponent from './components/Footer.vue'
import CurrentData from './services/Current.vue'
import ForecastVue from './components/Forecast.vue'
</script>

<template>
  <header>
    <!-- <h4></h4>
    <div class="wrapper">
      <HelloWorld msg="Weather App" />
    </div> -->
    <NavComponent/>
  </header>
  <FooterComponent/>
  <CurrentData/>
  <section class="main">
  <ForecastVue/>
  <p>Other Components</p>
  </section>
</template>

<style scoped>
  .main{
    display: flex;
    justify-content:center;
    /* padding: 7vh; */


  }
</style>
