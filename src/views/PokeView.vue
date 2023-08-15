<script setup>
import { useRoute, useRouter } from 'vue-router';
import { useGetData } from '@/composables/getData';
import { useFavoritosStore } from '@/stores/favoritos';

const route = useRoute();
const router = useRouter();
const useFavoritos = useFavoritosStore();

const { add, findPoke } = useFavoritos;

const back = () => {
    router.push('/pokemons');
}

const { data, getData, loading, error } = useGetData();

getData(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`); 
</script>

<template>
    <p v-if="loading">Cargando información...</p>
    <div class="alert alert-danger mt-2" v-if="error">{{ error }}</div>
    <div v-if="data" class="text-center">
        <img :src="data.sprites?.front_shiny" alt="">
        <h2>Poke name: {{ $route.params.name }}</h2>
        <button :disabled="findPoke(data.name)" @click="add(data)" class="btn btn-outline-danger mb-2">agregar favorito</button>
    </div>
    <div class="text-center mt-2">
        <button @click="back" class="btn btn-outline-dark">volver</button>
    </div>
</template>