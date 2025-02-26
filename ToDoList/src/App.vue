<template>
  <h1>ToDoList</h1>

  <form @submit.prevent="addTask">
    <fieldset>
      <input v-model="newTask" type="text" placeholder="Entrez une nouvelle tâche">
      <button :disabled="newTask.length === 0">Ajouter la tâche</button>
    </fieldset>
  </form>

  <!--Correction-->

<div v-if="tasks.length === 0">
  Vous n'avez pas de tâches à faire !
</div>
<div v-else>
  <ul>
    <li 
      v-for="task in sortedTasks()"
      :key="task.title"
      :class="{completed: task.completed}"
      >
    <label>
      <input type="checkbox" v-model="task.completed">
      {{ task.title }}
    </label>
    </li>
  </ul>
  <label>
    <input type="checkbox" v-model="hideCompleted">
    Masquer les tâches complétées
  </label>
</div>
</template>

<script setup>
import {ref} from 'vue'

const tasks = ref([
  { title: "Acheter la propriété 'Rue de la Paix'", completed: false, date: 20240730 },
  { title: "Construire un hôtel sur 'Avenue Foch'", completed: false, date: 20240730 },
  { title: "Éviter la case prison", completed: false, date: 20240730 }
])

const newTask = ref('') // Variable pour stocker l'entrée utilisateur
const hideCompleted = ref(false)

const addTask = () => {
  if (newTask.value.trim() === '') return // Vérifie si l'entrée est vide

  tasks.value.push({
    title: newTask.value,
    completed: false,
    date: new Date().toISOString().split('T')[0] // Ajoute la date du jour
  })

  newTask.value = '' // Réinitialise l'input
}

const sortedTasks = () => {
  const sortedTasks = tasks.value.toSorted((a,b) => a.completed > b.completed ? 1 : -1)
  if (hideCompleted.value === true) {
    return sortedTasks.filter(t => t.completed === false)
  }
  return sortedTasks
}


</script>

<style>
.completed {
  opacity: .5;
  text-decoration: line-through;
}
</style>
