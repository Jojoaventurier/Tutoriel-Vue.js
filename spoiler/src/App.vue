<template>
  <button @click="toggleSpoiler">Afficher / Masquer le spoiler</button>
  <div v-if="showSpoiler" class="spoiler">
    A la fin de la série, Marc Cunningan meurt !
  </div>
</template>

<script setup>
import { ref } from 'vue';

const showspoiler = ref(false)
const toggleSpoiler = () => showspoiler.value = !showspoiler.value
</script>