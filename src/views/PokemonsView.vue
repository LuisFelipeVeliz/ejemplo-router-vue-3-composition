<script setup>
import axios from 'axios';
import { ref } from 'vue';
import { RouterLink } from 'vue-router';

const pokemons = ref([]);
const getData = async () => {
    try {
       const { data } = await axios.get("https://pokeapi.co/api/v2/pokemon");
       pokemons.value = data.results;
    } catch (error) {
        console.log(error);
    }
}

getData();

</script>

<template>
    <h2>Pokémons</h2>
    <ul>
        <li v-for="pokemon in pokemons">
            <RouterLink :to="`/pokemons/${pokemon.name}`">{{ pokemon.name }}</RouterLink>
        </li>
    </ul>
</template>