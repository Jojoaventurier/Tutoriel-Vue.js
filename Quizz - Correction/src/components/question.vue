<template>
    <div class="question">
        <h3>{{ question }}</h3>
    </div>
</template>

<script setup>
defineProps({
    question: Object
})
</script>