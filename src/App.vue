<script setup>
import { ref } from 'vue'
const newtask = ref('')
const tasks = ref([])

const addTask = () => {
  const text = newtask.value.trim()
  if (!text) {
    return
  }

  tasks.value.push({
    id: Date.now(),
    text: text,
    completed: false,
    favorite: false
  });

  newtask.value = ''
  console.log(tasks);

}

const removeTask = (id) => {
    tasks.value = tasks.value.filter((t)=>t.id != id)
  }
</script>

<template>
  <div class="wrapper">
    <h1>Todo App</h1>
    <div class="input-row">
      <input type="text" placeholder="Add Task here..." v-model="newtask">
      <button @click="addTask">Add</button>
    </div>

    <ul class="task-list">
      <li v-for="task in tasks" :key="task.id" :class="{done: task.completed}">
        <button class="delete" @click="removeTask(task.id)">X</button>
        <input type="checkbox" v-model="task.completed">
        <span>{{ task.text }}</span>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.app {
  max-width: 500px;
  margin: 2rem;
  font-family: Arial, Helvetica, sans-serif;
  text-align: center;
}

.input-row {
  display: flex;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

input {
  flex-grow: 1;
  border: 1px solid #ccc;
  border-radius: 6px;
  padding: 0.5rem;
}

button {
  border: 1px solid #ccc;
  border-radius: 6px;
  padding: 0.5rem 1rem;
  cursor: pointer;
}

.task-list{
  list-style: none;
  padding: 0;
}

.task-list li{
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 0.5rem;
  padding: 0.5rem;
  border-bottom: 1px solid #ccc;
}

.task-list li.done span{
  text-decoration: line-through;
  opacity: 0.6;
}
.delete{
  background: #e53e3e;
  color: white;
  border:none;
  border-radius: 4px;
}
.delete:hover{
  background: #c53030;
}
</style>
