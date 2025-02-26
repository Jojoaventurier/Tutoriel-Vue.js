<template>
  <h1>ToDoList</h1>

  <ul>
    <li 
    v-for="task in taskListTest"
    :key="task"
    >
      {{ task.title }}
      {{ task.date }} 
      <button @click="deleteMovie(movie)">Supprimer</button>

    </li>
  </ul>
</template>


<script setup>

const taskListTest = [
    { "title": "Acheter la propriété 'Rue de la Paix'", "completed": false, "date": 20240730 },
    { "title": "Construire un hôtel sur 'Avenue Foch'", "completed": false, "date": 20240730 },
    { "title": "Éviter la case prison", "completed": false, "date": 20240730 }
]

</script>



