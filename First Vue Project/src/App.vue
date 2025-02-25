<template>
  <p>Compteur : {{ count }}</p>
</template>

<script setup>
import {ref} from 'vue'

const count = ref(0)
count.value = 3
</script>
