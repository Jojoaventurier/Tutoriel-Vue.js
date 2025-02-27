<template>
<label>
    <input type="checkbox" v-model="model"> <!--@onChange="onChange"-->
    {{ label }}
</label>
</template>

<script setup>
const model = defineModel() //pas besoin d'importer defineModel()
defineProps({ // pas besoin d'importer defineProps()
    label: String
})
const emits = defineEmits(['check', 'uncheck'])
const onChange = (event) => {
    if (event.currentTarget.checked) {
        emits('check', event.currentTarget)
    } else {
        emits('uncheck', event.currentTarget)
    }
}

</script>