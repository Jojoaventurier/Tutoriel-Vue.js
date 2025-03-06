<template>
    <div class="question">
        <h3>{{ question.question }}</h3>
        <ul>
            <li v-for="choice in question.choices" :key="choice">{{ choice }}</li>
        </ul>
    </div>
</template>

<script setup>
const props = defineProps({
    question: Object
})
</script>

<style>
.question {
    padding-top: 2rem
}
</style>