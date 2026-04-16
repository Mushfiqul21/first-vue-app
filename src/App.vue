<script setup>
import { ref } from 'vue'
const counter = ref('0')
const dec = () => {
  if (counter.value > 0) {
    counter.value--
  }
}
</script>

<template>
  <h1>Counter is: {{ counter }}</h1>
  <button @click = "counter++">increment +1</button>
  <button @click = "dec">decrement -1</button>

</template>

<style scoped></style>
