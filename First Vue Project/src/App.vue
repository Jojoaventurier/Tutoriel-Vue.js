<template>
  <p :id="`p-${count}`">Compteur : {{ count }}</p>

  <p :style="{color: count >= 5 ? 'green' : 'red'}">style dynamique</p>
  <p :class="{active: count >= 5}">Actif dynamique</p>

  <div v-if="count >= 5">Bravo vous avez cliqué plus de 5 fois</div>
  <div v-else>Vous avez cliqué moins de cinq fois</div>

  <button v-on:click="increment">Incrémenter</button>
  <button v-on:click="decrement">Décrémenter</button>
  <hr>
  <button @click="sortMovies">Réorganiser</button>
  <form action="" @submit.prevent="addMovie">
    <input type="text" placeholder="Nouveau film"
    v-model="movieName">
    {{ movieName }}
    <button>Ajouter le film</button>
  </form>

  <ul>
    <li 
    v-for="movie in movies"
    :key="movie"
    >
      {{ movie }} <button @click="deleteMovie(movie)">Supprimer</button>
    </li>
  </ul>

<ul>
  <li>{{ person.firstName }}</li>
  <li>{{ person.lastName }}</li>
  <li>{{ person.age }}</li>
</ul>
<button @click.prevent="randomAge()">Changer âge</button>
<button @click.prevent="randomAgeButSimpler()">Changer âge aussi</button>
</template>

<script setup>
import {ref} from 'vue'

const person = ref({
  firstName: 'Jojo',
  lastName: 'Aventurier',
  age: 20
})
const count = ref(0)
const movieName = ref('')
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

const sortMovies = () => {
  movies.value.sort((a,b) => a > b ? 1 : -1)
}

const addMovie = () => {
  movies.value.push(movieName.value)
  movieName.value = ""
}

const randomAge = () => {
  person.value = {
    ...person.value,
    age: Math.round(Math.random() * 100)
  }
}
//or 
const randomAgeButSimpler = () => {
    person.value.age = Math.round(Math.random() * 100)
}

</script>
