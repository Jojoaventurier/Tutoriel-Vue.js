<template>
    <div>
        Temps : {{ time }}
    </div>
</template>

<script setup>
import {ref, onMounted, onUnmounted} from 'vue';

const time = ref(0)

let timer

onMounted(() => {
    timer = setInterval(() => {
        time.value++
    }, 1_000)
})
// important d'unmount si on a des composants qui ont une logique, si on les masque par exemple, afin de nettoyer et éviter les fuites de mémoires qui peuvent affecter les performances
onUnmounted(() => {
    clearInterval(timer)
})

</script>