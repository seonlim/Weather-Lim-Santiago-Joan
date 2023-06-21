<script setup>
import HelloWorld from './components/HelloWorld.vue'
import NavComponent from './components/NavBar.vue'
import FooterComponent from './components/Footer.vue'
import Header from './components/Header.vue'
import CurrentData from './services/Current.vue'
import ForecastVue from './components/Forecast.vue'
</script>

<template>
    <Header/>
    <NavComponent/>
  <FooterComponent/>
  <CurrentData/>
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
