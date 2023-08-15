<script setup>
import { RouterLink } from 'vue-router';
import { useGetData } from '@/composables/getData';

const { data, getData, loading, error } = useGetData();

getData("https://pokeapi.co/api/v2/pokemon");
</script>

<template>
    <h2>Pokémons</h2>
    <p v-if="loading">Cargando información...</p>
    <div class="alert alert-danger mt-2" v-if="error">{{ error }}</div>
    <div v-if="data">
        <ul class="list-group">
            <li class="list-group-item" v-for="pokemon in data.results">
                <RouterLink :to="`/pokemons/${pokemon.name}`">{{ pokemon.name }}</RouterLink>
            </li>
        </ul>
        <div class="mt-2">
            <button :disabled="!data.previous" class="btn btn-outline-dark me-2" @click="getData(data.previous)">Prev</button>
            <button :disabled="!data.next" class="btn btn-outline-dark" @click="getData(data.next)">Next</button>
        </div>
    </div>
</template>