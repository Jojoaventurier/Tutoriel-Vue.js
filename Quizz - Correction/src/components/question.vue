<template>
    <div class="question">
        <h3>{{ question.question }}</h3>
        <ul>
            <li v-for="(choice, index) in question.choices" :key="choice"> <!--on peut ajouter index dans le for pour le récupérer ensuite et le mettre en id par exemple-->
                <label :for="`answer${index}`"> <!--on pense bien à lier l'id de l'input au for du label pour l'accessibilité-->
                    <input :id="`answer${index}`" type="radio" name="answer" v-model="answer" :value="choice">
                    {{ choice }}
                </label>
            </li>
        </ul>
        <button :disabled="!hasAnswer" @click="emits('answer', answer)">Question suivante</button>
    </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const props = defineProps({
    question: Object
})
const emits = defineEmits(['answer'])
const answer = ref(null)
const hasAnswer = computed(() => answer.value !== null) // utilisée pour désactiver le bouton "Question suivante" aucune réponse n'a été choisie
</script>

<style>
.question {
    padding-top: 2rem
}

.question button {
    margin-left:auto auto;
    display: block;
}
</style>