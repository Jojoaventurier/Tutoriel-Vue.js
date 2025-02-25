<template>
  <p :id="`p-${count}`">Compteur : {{ count }}</p>

  <p :style="{color: count >= 5 ? 'green' : 'red'}">style dynamique</p>
  <p :class="{active: count >= 5}">Actif dynamique</p>

  <div v-if="count >= 5">Bravo vous avez cliqué plus de 5 fois</div>
  <div v-else>Vous avez cliqué moins de cinq fois</div>

  <button v-on:click="increment">Incrémenter</button>
  <button v-on:click="decrement">Décrémenter</button>

  <ul>
    <li v-for="movie in movies">
      {{ movie }} <button @click="deleteMovie(movie)">Supprimer</button>
    </li>
  </ul>
</template>

<script setup>
import {ref} from 'vue'

const count = ref(0)
const movies = ref([
  'Matrix',
  'Alien',
  'Blade Runner'
])
const increment = () => {
  count.value++
}

const decrement = () => {
  count.value--
}

const deleteMovie = (movie) => {
  movies.value = movies.value.filter (m => m != movie)
}

</script>
