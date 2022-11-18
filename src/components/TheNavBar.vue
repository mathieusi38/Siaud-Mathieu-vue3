<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
    <nav id="nav">
      <ul>
        <li class="current"> <RouterLink to="/">Home</RouterLink></li>

        <!-- <li><a href="left-sidebar.html">Pokémons</a></li> -->
        <li><RouterLink to="/liste">Liste Amiibo</RouterLink></li>
      </ul>
    </nav>
</template>

<style scoped>

</style>
