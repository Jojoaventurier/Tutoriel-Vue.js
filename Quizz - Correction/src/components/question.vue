<template>
    <div class="question">
        <h3>{{ question.question }}</h3>
        <ul>
            <li v-for="(choice, index) in randomChoices" :key="choice"> <!--on peut ajouter index dans le for pour le récupérer ensuite et le mettre en id par exemple-->
                <Answer :id="`answer${index}`"
                        :disabled="hasAnswer"
                        :value="choice"
                        v-model="answer"
                        :correctAnswer="question.correct_answer"/>
            </li>
        </ul>
       </div>
</template>

<script setup>
import { ref, computed, onMounted } from 'vue';
import { shuffleArray } from '@/functions/array.js';
import Answer from './answer.vue';

const props = defineProps({
    question: Object
})
const emit = defineEmits(['answer'])
const answer = ref(null)
const hasAnswer = computed(() => answer.value !== null) // utilisée pour désactiver le bouton "Question suivante" aucune réponse n'a été choisie
const randomChoices = computed(() => shuffleArray(props.question.choices))

let timer

onMounted(() => {
    timer = setTimeout(() => {
        emit('answer', answer.value)
    }, 3_000)
})


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