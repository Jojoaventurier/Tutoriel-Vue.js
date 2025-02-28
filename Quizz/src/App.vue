<script setup>
import { ref, onMounted } from 'vue' // Importation de ref pour les variables réactives et onMounted pour exécuter du code après le montage du composant
import HeaderQuizz from './components/HeaderQuizz.vue' // Importation du composant pour l'en-tête
import QuestionBox from './components/QuestionBox.vue' // Importation du composant des questions

// Variables réactives
const quizz = ref(null) // Stocke les données JSON du quizz
const currentQuestion = ref(0) // Indice de la question actuelle (commence à 0)
const score = ref(0) // Score de l'utilisateur

// Cette fonction s'exécute automatiquement lorsque le composant est monté
onMounted(async () => {
  const response = await fetch('/quizz.json') // Récupération du fichier JSON
  quizz.value = await response.json() // Stocke les données dans la variable quizz
})

// Fonction pour passer à la question suivante
const nextQuestion = (isCorrect) => {
  if (isCorrect) {
    score.value++ // Si la réponse est correcte, on ajoute 1 au score
  }

  // Vérifie si on est à la dernière question
  if (currentQuestion.value < quizz.value.questions.length - 1) {
    currentQuestion.value++ // Passe à la question suivante
  } else {
    alert(`Quizz terminé ! Score : ${score.value}/${quizz.value.questions.length}`) // Affiche le score final
  }
}
</script>

<template>
  <header>
    <div class="wrapper">
      <HeaderQuizz msg="Questionnaire sur les films et les séries" />
    </div>
  </header>

  <main>
    <div v-if="quizz"> <!-- Affiche les questions seulement si les données sont chargées -->
      <QuestionBox
        :question="quizz.questions[currentQuestion].question" 
        :choices="quizz.questions[currentQuestion].choices" 
        :correctAnswer="quizz.questions[currentQuestion].correct_answer" 
        @answerValidated="nextQuestion" 
      />
    </div>
    <div v-else>
      Chargement... <!-- Affiche "Chargement" pendant que les données se chargent -->
    </div>
  </main>
</template>


