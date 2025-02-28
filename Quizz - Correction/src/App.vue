<template>
  <div v-if="state === 'error'">
    <p>
        Impossible de charger le quiz !
    </p>
  </div>
  <div :aria-busy="state === 'loading'">
    {{ quiz }}
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';

const quiz = ref(null)
const state = ref('loading')

onMounted(() => {
  fetch('/quiz.json')
    .then(r.ok) {
      if (r.ok) {
        return r.json()
      }
      throw new Error('Impossible de récupérer le fichier json')
    })
    .then (data => {
      quiz.value = data
      state.value = 'idle'
    })
    .catch(e => {
      state.value = 'error'
    })
})
</script>


