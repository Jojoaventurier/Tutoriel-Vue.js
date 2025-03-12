<template>
  <h2>Compteur</h2>
  <p>
    Compteur : {{ count }} x 2 = {{ double }}
  </p>
  <button @click="increment">Increment</button>
</template>

<script setup>
  import { computed, ref } from 'vue';

  const count = ref(0)
  const double = comptued(() => count.value * 2)
  const increment = () => count.value++
</script>