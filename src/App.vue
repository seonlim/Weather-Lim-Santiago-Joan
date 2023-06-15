<script setup>
import HelloWorld from './components/HelloWorld.vue'
import NavComponent from './components/NavBar.vue'
import FooterComponent from './components/Footer.vue'
import Header from './components/Header.vue'
</script>

<template>
    <Header/>
    <NavComponent/>
  <FooterComponent/>
</template>

<style scoped>
#app{
  align-items: center;
  justify-content: center;
}
</style>
