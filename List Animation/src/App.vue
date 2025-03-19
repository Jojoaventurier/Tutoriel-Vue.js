<template>
  <form role="group" @submit.prevent="addMovie">
    <input type="text" v-model="movie">
    <button :disabled="movie.length === 0 ">Ajouter</button>
  </form>

    <TransitionGroup name="list" tag="ul"> <!--TransitionGroup ne fonctionne que si il a un enfant avec un v-for-->
      <!--On peut ajouter un tag="ul" pour ne pas avoir à mettre de balise ul en plus autour des <li>-->
      <!--Les modes n'ont pas de sens pour un TransitionGroup-->
      <li v-for="movie in movies" :key="movie">
        {{ movie }}
        <button class="secondary" @click="removeMovie(movie)">x</button>
      </li>
    </TransitionGroup>

    <button @click="randomize">Réorganiser</button>
</template>

<script setup>
import { ref } from 'vue';

const shuffleArray = (array) => {
    let shuffledArray = array.slice(); // Copie du tableau pour éviter de modifier l'original
    for (let i = shuffledArray.length - 1; i > 0; i--) {
        let j = Math.floor(Math.random() * (i + 1));
        [shuffledArray[i], shuffledArray[j]] = [shuffledArray[j], shuffledArray[i]]; // Échange des éléments
    }
    return shuffledArray;
}

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
  movies.value = [movie.value, ...movies.value]
  movie.value = ''
}
const removeMovie = (movie) => {
  movies.value = movies.value.filter(m => m !== movie)
}

const randomize = () => {
  movies.value = shuffleArray(movies.value)
}
</script> 

<style>
.list-move,
.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}

.list-leave-active {
  position: absolute;
}

.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}
</style>