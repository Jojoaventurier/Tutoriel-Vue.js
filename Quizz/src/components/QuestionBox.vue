<script setup>
import { ref } from 'vue' // Importation de ref pour rendre les variables réactives

// Définition des propriétés reçues du parent
const props = defineProps({
  question: { type: String, required: true }, // Texte de la question
  choices: { type: Array, required: true },   // Liste des choix possibles
  correctAnswer: { type: String, required: true } // Bonne réponse
})

// Variable réactive pour stocker la réponse sélectionnée
const selectedAnswer = ref('')
const isDisabled = ref(true) // Le bouton est désactivé tant qu'aucune réponse n'est sélectionnée

// Permet d'émettre des événements vers le parent
const emit = defineEmits(['answerValidated'])

// Fonction appelée à chaque sélection pour activer/désactiver le bouton
const selectAnswer = () => {
  isDisabled.value = selectedAnswer.value === '' // Active le bouton si une réponse est sélectionnée
}

// Fonction pour valider la réponse
const validateAnswer = () => {
  const isCorrect = selectedAnswer.value === props.correctAnswer // Vérifie si la réponse est correcte
  emit('answerValidated', isCorrect) // Envoie l'événement au parent avec la réponse
  selectedAnswer.value = '' // Réinitialise la réponse sélectionnée
  isDisabled.value = true // Désactive à nouveau le bouton
}
</script>

<template>
  <div>
    <h2>{{ question }}</h2> <!-- Affiche la question -->
    <ul>
      <li v-for="(choice, i) in choices" :key="i"> <!-- Boucle pour afficher toutes les réponses -->
        <label>
          <input
            type="radio"
            :value="choice"
            :class="{'text-green-500': selectedAnswer === correctAnswer, 'text-red-500': selectedAnswer !== correctAnswer && selectedAnswer !== ''}"
            v-model="selectedAnswer" 
            @change="selectAnswer" 
            name="answer"
          />
          <!-- v-model="" Lie la réponse sélectionnée -->
          <!-- @change Déclenche la fonction à chaque sélection -->
          {{ choice }}
        </label>
      </li>
    </ul>

    <!-- Bouton Valider -->
    <!-- Bouton désactivé tant qu'aucune réponse n'est choisie -->
    <button 
      :disabled="isDisabled" 
      @click="validateAnswer"
      class="bg-blue-500 text-white p-2 rounded">
      Valider
    </button>
  </div>
</template>

<style scoped>
.item {
  margin-top: 2rem;
  display: flex;
  position: relative;
}

.details {
  flex: 1;
  margin-left: 1rem;
}

i {
  display: flex;
  place-items: center;
  place-content: center;
  width: 32px;
  height: 32px;

  color: var(--color-text);
}

h3 {
  font-size: 1.2rem;
  font-weight: 500;
  margin-bottom: 0.4rem;
  color: var(--color-heading);
}

@media (min-width: 1024px) {
  .item {
    margin-top: 0;
    padding: 0.4rem 0 1rem calc(var(--section-gap) / 2);
  }

  i {
    top: calc(50% - 25px);
    left: -26px;
    position: absolute;
    border: 1px solid var(--color-border);
    background: var(--color-background);
    border-radius: 8px;
    width: 50px;
    height: 50px;
  }

  .item:before {
    content: ' ';
    border-left: 1px solid var(--color-border);
    position: absolute;
    left: 0;
    bottom: calc(50% + 25px);
    height: calc(50% - 25px);
  }

  .item:after {
    content: ' ';
    border-left: 1px solid var(--color-border);
    position: absolute;
    left: 0;
    top: calc(50% + 25px);
    height: calc(50% - 25px);
  }

  .item:first-of-type:before {
    display: none;
  }

  .item:last-of-type:after {
    display: none;
  }
}
</style>
