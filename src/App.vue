<script setup>
import { RouterLink, RouterView } from 'vue-router'
import TheNavBar from './components/TheNavBar.vue'
import TheBanner from './components/TheBanner.vue';
import TheFooter from './components/TheFooter.vue';
</script>

<template>

  <div id="page-wrapper">

  <section id="header">

      <!-- Logo -->
        <h1><RouterLink to="/">AmiiVue</RouterLink></h1>

      <!-- Nav -->
      <TheNavBar />

      <RouterView />
      <TheFooter />

</section>
</div>

</template>

<style scoped>

</style>
