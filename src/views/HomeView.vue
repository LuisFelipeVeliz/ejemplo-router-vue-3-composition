<script setup>
import { useCounterStore } from '@/stores/counter';
import { storeToRefs } from 'pinia';

const useCounter = useCounterStore();
const { count, double } = storeToRefs(useCounter);
const { increment } = useCounterStore();

</script>

<template>
  <h1>Home counter: {{ count }}</h1>
  <h2>Double: {{ double }}</h2>
  <button @click="increment">increment</button>
</template>
