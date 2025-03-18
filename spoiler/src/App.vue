<template>
  <button @click="toggleSpoiler">Afficher / Masquer le spoiler</button>

  <FadeSlideTransition name="fadeSlide"> <!--VOIR DOCUMENTATION CSS-BASED TRANSITIONS-->
    <div v-if="showSpoiler" class="spoiler">
      A la fin de la série, Marc Cunningan meurt !
    </div>
  </FadeSlideTransition>
</template>

<script setup>
import { ref } from 'vue';
import FadeSlideTransition from './FadeSlideTransition.vue';

const showSpoiler = ref(false)
const toggleSpoiler = () => showSpoiler.value = !showSpoiler.value
</script>


<style>
  .spoiler {
    padding: 1rem;
    border: 1px solid #c42626de;
    transition: .5s;
  }
</style>