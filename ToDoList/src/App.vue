<template>
  <h1>ToDoList</h1>

  <form @submit.prevent="addTask">
    <fieldset>
      <input v-model="newTask" type="text" placeholder="Entrez une nouvelle tâche">
      <button :disabled="newTask.length === 0">Ajouter la tâche</button>
    </fieldset>
  </form>

  <h2>À faire</h2>
  <div v-if="incompleteTasks.length === 0">Vous n'avez pas de tâches en cours !</div>
  <ul>
    <li v-for="task in incompleteTasks" :key="task.date">
      {{ task.title }} - {{ task.date }} 
      <button @click="completeTask(task)">Effectué !</button>
      <button @click="deleteTask(task)">Supprimer</button>
    </li>
  </ul>

  <h2>Terminées</h2>
  <ul>
    <li v-for="task in completedTasks" :key="task.title">
      {{ task.title }} - {{ task.date }} 
      <button @click="deleteTask(task)">Supprimer</button>
    </li>
  </ul>
</template>

<script setup>
import { ref, computed } from 'vue'

const tasks = ref([
  { title: "Acheter la propriété 'Rue de la Paix'", completed: false, date: 20240730 },
  { title: "Construire un hôtel sur 'Avenue Foch'", completed: false, date: 20240730 },
  { title: "Éviter la case prison", completed: false, date: 20240730 }
])

const newTask = ref('') // Variable pour stocker l'entrée utilisateur

const deleteTask = (task) => {
  tasks.value = tasks.value.filter(t => t.title !== task.title)
}

const addTask = () => {
  if (newTask.value.trim() === '') return // Vérifie si l'entrée est vide

  tasks.value.push({
    title: newTask.value,
    completed: false,
    date: new Date().toISOString().split('T')[0] // Ajoute la date du jour
  })

  newTask.value = '' // Réinitialise l'input
}

const completeTask = (task) => {
  tasks.value = tasks.value.map(t => 
    t.title === task.title ? { ...t, completed: true } : t
  );
};

const incompleteTasks = computed(() => tasks.value.filter(task => !task.completed));
const completedTasks = computed(() => tasks.value.filter(task => task.completed));

</script>
