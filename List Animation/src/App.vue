<template>
  <form role="group" @submit.prevent="addMovie">
    <input type="text" v-model="movie">
    <button :disabled="movie.length === 0 ">Ajouter</button>
  </form>
  <ul>
    <TransitionGroup name=""> <!--TransitionGroup ne fonctionne que si il a un enfant avec un v-for-->
      <li v-for="movie in movies" :key="movie">
        {{ movie }}
        <button class="secondary" @click="removeMovie(Movie)">x</button>
      </li>
  </TransitionGroup>
  </ul>
</template>

<script setup>
import { ref } from 'vue';

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
  movies.value.push(movie.value)
  movie.value = ''
}
const removeMovie = (movie) => {
  movies.value = movies.value.filter(m => m !== movie)
}
</script> 

<style>
.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}

.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}
</style>