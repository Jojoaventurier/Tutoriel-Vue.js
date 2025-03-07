<template>
    <label :for="id"> <!--on pense bien à lier l'id de l'input au for du label pour l'accessibilité-->
        <input :disabled="disabled" :id="id" type="radio" name="answer" v-model="model" :value="value">
        {{ value }}
    </label>
</template>

<script setup>
const props = defineProps({
    id: String,
    disabled: Boolean,
    value: String,
})
const model = defineModel()
</script>