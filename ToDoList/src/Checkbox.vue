<template>
<label>
    <input type="checkbox">
    Lorem ipsum dolor
</label>
</template>

<script setup>
const props = defineProps({ // pas besoin d'importer defineProps()
    label: String
})
console.log(props.label)
</script>