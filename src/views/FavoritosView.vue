<script setup>
import { useFavoritosStore } from '@/stores/favoritos';
import { storeToRefs } from 'pinia';
import { RouterLink } from 'vue-router';

const useFavoritos = useFavoritosStore();

const { favoritos } = storeToRefs(useFavoritos);
const { remove } = useFavoritos;
</script>

<template>
    <h1>Favoritos</h1>
    <p v-if="favoritos.length === 0">Sin favoritos</p>
    <ul v-else class="list-group">
        <li class="list-group-item" v-for="pokemon in favoritos" :key="pokemon.id">
            <div>
                <h4>{{ pokemon.name }}</h4>
            </div>
            <div class="mb-2">
                <RouterLink :to="`/pokemons/${pokemon.name}`" class="btn btn-outline-info btn-sm">Más información</RouterLink>
            </div>
            <div>
                <button @click="remove(pokemon.id)" class="btn btn-outline-secondary btn-sm">Eliminar</button>
            </div>
        </li>
    </ul>
</template>