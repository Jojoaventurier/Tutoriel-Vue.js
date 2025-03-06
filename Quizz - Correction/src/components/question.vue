<template>
    <div class="question">
        <h3>{{ question.question }}</h3>
    </div>
</template>

<script setup>
const props = defineProps({
    question: Object
})
</script>