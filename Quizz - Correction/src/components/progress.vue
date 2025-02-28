<template>
    <div>
        Etape {{ value + 1 }}/{{ max + 1 }}
    </div>
</template>

<script setup>
defineProps({
    value: Number,
    max: Number
})
</script>