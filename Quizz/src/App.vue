<script setup>
import HeaderQuizz from './components/HeaderQuizz.vue'
import QuestionBox from './components/QuestionBox.vue'
</script>

<template>
  <header>
    <div class="wrapper">
      <HeaderQuizz msg="Questionnaire sur les films et les séries" />
    </div>
  </header>

  <main>
    <QuestionBox question="Voici la question ?" answer="Voici une réponse !" />
  </main>
</template>


