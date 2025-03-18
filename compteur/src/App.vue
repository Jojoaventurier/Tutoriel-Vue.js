<template>
  <h2>Compteur</h2>
  <p>
    Compteur : {{ count }} x 2 = {{ double }}
  </p>
  <button @click="increment">Increment</button>
</template>

<script setup>
  import { computed, ref, shallowRef, toRaw } from 'vue';
  import { useCounter } from './composable/useCounter.js';

  const { count, increment } = useCounter()
  const raw = {
    firstname: 'John',
    lastname: 'Doe'
  }

  const raw2 = reactive({
    firstname: 'John',
    lastname: 'Doe'
  })


  const person = ref(raw)
  const person2 = shallowRef(raw) // REVOIR
  const person3 = ref(markRaw(raw)) // REVOIR
  console.log(person3.value, person2.value, person.value === raw)
  console.log(toRaw(person.value) === raw)
  const double = computed(() => count.value * 2) // REVOIR
  //VOIR REACTIVITY IN DEPTH IN VUE.JS DOCUMENTATION

  const realPerson = ref({
    firstName : 'Jojo',
    lastName: 'Aventurier'
  })
</script>