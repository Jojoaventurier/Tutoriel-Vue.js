<template>
  <h2>Compteur</h2>
  <p>
    Compteur : {{ count }} x 2 = {{ double }}
  </p>
  <button @click="increment">Increment</button>
</template>

<script setup>
  import { computed, ref } from 'vue';
  import { useCounter } from './composable/useCounter.js';

  const { count, increment } = useCounter()
  const person = ref({
    firstname: 'John',
    lastname: 'Doe'
  })
  console.log(person)
  const double = computed(() => count.value * 2)
</script>