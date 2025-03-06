<template>
    <div>
        <h1>{{ quiz.title }}</h1>
        <Progress :value="step" :max="quiz.questions.length - 1"/>
        <Question :question="question" v-if="question"/>
    </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import Progress from './progress.vue'
import Question from './question.vue'

const props = defineProps ({
    quiz: Object
})

const step = ref(0)
const question = computed(() => props.quiz.questions[step.value]) // step est une valeur réactive, il faut donc écrire step.value

</script>