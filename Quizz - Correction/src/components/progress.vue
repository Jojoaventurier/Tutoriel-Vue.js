<template>
    <div>
        Etape {{ value }}/{{ max }}
    </div>
</template>

<script setup>
defineProps({
    value: Number,
    max: Number
})
</script>