<template>
    <label :for="id" :class="classes"> <!--on pense bien à lier l'id de l'input au for du label pour l'accessibilité-->
        <input :disabled="disabled" :id="id" type="radio" name="answer" v-model="answer" :value="value" @change="onChange">
        {{ value }}
    </label>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
    id: String,
    disabled: Boolean,
    value: String,
    correctAnswer: String
})
const emit = defineEmits(['change'])
const onChange = (event) => {
    emit('change', event)
}
const model = defineModel()
const classes = computed(() => ({
    disabled : props.disabled,
    right: props.disabled && props.value === props.correctAnswer,
    wrong: props.disabled && props.value !== props.correctAnswer && model.value === props.value
}))
</script>

<style>
.disabled {
    opacity: .5;
}
.right {
    opacity: 1;
    color: green;
}
.wrong {
    opacity: 1;
    color: red;
}
</style>