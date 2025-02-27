<template>
    <div ref="div">
        Temps : {{ time }}<br/>
        Largeur : {{ size.width }}, Hauteur: {{ size.height }}
    </div>
</template>

<script setup>
import {ref, onMounted, onUnmounted} from 'vue';

const div = ref(null)
const time = ref(0)
const size = ref({width: 0, height: 0})

let timer
onMounted(() => {
    const rect = div.value.getBoundingClientRect()
    size.value = {width: rect.width, height: rect.height}
    timer = setInterval(() => {
        time.value++
    }, 1_000)
})
// important d'unmount si on a des composants qui ont une logique, si on les masque par exemple, afin de nettoyer et éviter les fuites de mémoires qui peuvent affecter les performances
onUnmounted(() => {
    clearInterval(timer)
})

</script>