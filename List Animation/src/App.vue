<template>
  <form role="group" @submit.prevent="addMovie">
    <input type="text" v-model="movie">
    <button :disabled="movie.length === 0 ">Ajouter</button>
  </form>

    <TransitionGroup name="list" tag="ul"> <!--TransitionGroup ne fonctionne que si il a un enfant avec un v-for-->
      <!--On peut ajouter un tag="ul" pour ne pas avoir à mettre de balise ul en plus autour des <li>-->
      <li v-for="movie in movies" :key="movie">
        {{ movie }}
        <button class="secondary" @click="removeMovie(movie)">x</button>
      </li>
    </TransitionGroup>
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