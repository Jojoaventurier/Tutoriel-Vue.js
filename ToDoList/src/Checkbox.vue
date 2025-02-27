<template>
<label>
    <input type="checkbox">
    {{ label }}
</label>
</template>

<script setup>
defineProps({ // pas besoin d'importer defineProps()
    label: String
})

</script>