<template>
    <div>
        Temps : {{ time }}
    </div>
</template>

<script setup>
import {ref, onMounted} from 'vue';

const time = ref(0)

onMounted(() => {
    setInterval(() => {
        time.value++
    }, 1_000)
})

</script>