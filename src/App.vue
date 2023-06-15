<script setup>
import HelloWorld from './components/HelloWorld.vue'
import NavComponent from './components/NavBar.vue'
import FooterComponent from './components/Footer.vue'
import CurrentData from './services/Current.vue'
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
</template>

<style scoped>

</style>
