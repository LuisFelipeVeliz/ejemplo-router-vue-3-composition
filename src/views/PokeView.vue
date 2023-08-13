<script setup>
import axios from 'axios';
import { useRoute, useRouter } from 'vue-router';
import { ref } from 'vue';

const route = useRoute();
const router = useRouter();

const poke = ref({});

const back = () => {
    router.push('/pokemons');
}

const getData = async () => {
    try {
        const { data } = await axios.get(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`);
        poke.value = data;
    } catch (error) {
        console.log(error);
        poke.value = null;
    }
}

getData();
</script>

<template>
    <div v-if="poke" class="text-center">
        <img :src="poke.sprites?.front_shiny" alt="">
        <h2>Poke name: {{ $route.params.name }}</h2>
    </div>
    <h2 v-else>No existe el pokémon</h2>
    <div class="text-center mt-2">
        <button @click="back" class="btn btn-outline-dark">volver</button>
    </div>
</template>