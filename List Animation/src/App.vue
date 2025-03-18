<template>
  <form role="group" @submit.prevent="addMovie">
    <input type="text" v-model="movie">
    <button :disabled="movie.length === 0 ">Ajouter</button>
  </form>
  <ul>
    <li v-for="movie in movies" :key="movie">
      {{ movie }}
      <button class="secondary" @click="removeMovie(Movie)">x</button>
    </li>
  </ul>
</template>

<script setup>
import { ref } from 'vue';

const showSpoiler = ref(false)
const movies = ref([
  "Les Evadés",
  "Le Parrain",
  "Matrix",
  "Pulp Fiction",
  "Alien",
  "Terminator 2"
]);

const movie = ref('')
const addMovie = () => {
  
}
</script>