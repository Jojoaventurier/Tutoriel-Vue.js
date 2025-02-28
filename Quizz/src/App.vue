<script setup>
import { ref, onMounted } from 'vue'
import HeaderQuizz from './components/HeaderQuizz.vue'
import QuestionBox from './components/QuestionBox.vue'

const quizz = ref(null)

onMounted(async () => {
  const response = await fetch('/quizz.json')
  quizz.value = await response.json()
})
</script>

<template>
  <header>
    <div class="wrapper">
      <HeaderQuizz msg="Questionnaire sur les films et les séries" />
    </div>
  </header>

  <main>
    <div v-if="quizz">
      <QuestionBox 
        v-for="(q, index) in quizz.questions" 
        :key="index" 
        :question="q.question" 
        :choices="q.choices" 
        :index="index" 
      />
    </div>
    <div v-else>
      Chargement...
    </div>
  </main>
</template>


