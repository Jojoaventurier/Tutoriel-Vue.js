<template>
  <button @click="toggleSpoiler">Afficher / Masquer le spoiler</button>

  <Transition name="fadeSlide"> <!--VOIR DOCUMENTATION CSS-BASED TRANSITIONS-->
    <div v-if="showSpoiler" class="spoiler">
      A la fin de la série, Marc Cunningan meurt !
    </div>
  </Transition>
</template>

<script setup>
import { ref } from 'vue';

const showSpoiler = ref(false)
const toggleSpoiler = () => showSpoiler.value = !showSpoiler.value
</script>

<style>
.spoiler {
  padding: 1rem;
  border: 1px solid #c42626de;
  transition: .5s;
}
.fadeSlide-enter-from {
  opacity: 0;
  transform: translateX(10px);
}

.fadeSlide-leave-to {
  opacity: 0;
  transform: translateX(-10px);
}
</style>