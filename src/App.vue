<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <nav class="navbar bg-light">
    <div class="container">
      <RouterLink class="navbar-brand" to="/">
        <img src="@/assets/logo.svg" alt="Vue logo" width="30" height="24">
        PokeAPI
      </RouterLink>
      <div>
        <RouterLink class="btn btn-outline-primary me-1" to="/">Home</RouterLink>
        <RouterLink class="btn btn-outline-primary" to="/pokemons">Pokémons</RouterLink>
      </div>
    </div>
  </nav>

  <div class="container">
    <RouterView />
  </div>
</template>

<style>
</style>
