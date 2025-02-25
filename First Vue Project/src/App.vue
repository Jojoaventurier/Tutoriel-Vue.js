<template>
  <p :id="`p-${count}`">Compteur : {{ count }}</p>


<p :style="{color: count >= 5 ? 'green' : 'red'}">style dynamique</p>



  <div v-if="count >= 5">Bravo vous avez cliqué plus de 5 fois</div>
  <div v-else>Vous avez cliqué moins de cinq fois</div>
  <button v-on:click="increment">Incrémenter</button>
  <button v-on:click="decrement">Décrémenter</button>
</template>

<script setup>
import {ref} from 'vue'

const count = ref(0)
const increment = () => {
  count.value++
}

const decrement = () => {
  count.value--
}

</script>
