<template>
    <div class="question">
        <h3>{{ question.question }}</h3>
        <ul>
            <li v-for="(choice, index) in question.choices" :key="choice"> <!--on peut ajouter index dans le for pour le récupérer ensuite et le mettre en id par exemple-->
                <label :for="`answer${index}`"> <!--on pense bien à lier l'id de l'input au for du label pour l'accessibilité-->
                    <input :id="`answer${index}`" type="radio" name="answer">
                    {{ choice }}
                </label>
            </li>
        </ul>
    </div>
</template>

<script setup>
const props = defineProps({
    question: Object
})
</script>

<style>
.question {
    padding-top: 2rem
}
</style>