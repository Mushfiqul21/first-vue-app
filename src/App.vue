<script setup>
import { ref } from 'vue'
const newtask = ref('')
</script>

<template>
  <div class="wrapper">
    <h1>Todo App</h1>
    <div class="input-row">
      <input type="text" placeholder="Add Task here..." v-model="newtask">
      <button>Add</button>
    </div>
  </div>
</template>

<style scoped>
.app{
  max-width: 500px;
  margin: 2rem;
  font-family: Arial, Helvetica, sans-serif;
  text-align: center;
}
</style>
