<script setup>
import TodoItem from './components/TodoItem.vue'
import { nanoid } from 'nanoid'

const ToDoItems = [
  { id: 'todo-' + nanoid(), label: 'Learn Vue', done: false },
  { id: 'todo-' + nanoid(), label: 'Create a Vue project with the CLI', done: true },
  { id: 'todo-' + nanoid(), label: 'Have fun', done: true },
  { id: 'todo-' + nanoid(), label: 'Create a to-do list', done: false },
]
</script>

<template>
  <div id="app">
    <h1>To-Do List</h1>
    <ul>
      <li v-for="item in ToDoItems" :key="item.id">
        <TodoItem :label="item.label" :id="item.id" :done="item.done" />
      </li>
    </ul>
  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
