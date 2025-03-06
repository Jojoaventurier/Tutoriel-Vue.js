<template>
    <h1>Recap</h1>
</template>

<script setup>
const props = defineProps({
    quiz: Object,
    answers: Array
})

const score = computed(() => {
    return props.quiz.questions.reduce((acc, question, k) => {

    }, 0)
})
</script>