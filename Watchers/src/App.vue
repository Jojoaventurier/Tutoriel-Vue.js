<template>
  <input type="text" v-model="page.title">
</template>

<script setup>
import { ref, watch, watchEffect } from 'vue'

  const page = ref({
    title: ''
  })

  // watch(() => page.value.title, (newValue, oldValue) => {
  //   document.title = newValue
  // }, {immediate: true})

  watchEffect(() => {
    document.title = page.value.title
  })
</script>

