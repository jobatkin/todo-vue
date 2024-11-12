<script setup>
import { ref } from 'vue'
import TodoItem from './components/TodoItem.vue'
import TodoForm from './components/TodoForm.vue'
import TodoSort from './components/TodoSort.vue'
import { nanoid } from 'nanoid'

const toDoItems = ref([
  { id: 'todo-' + nanoid(), label: 'Learn Vue', done: false },
  { id: 'todo-' + nanoid(), label: 'Create a Vue project with the CLI', done: true },
  { id: 'todo-' + nanoid(), label: 'Have fun', done: true },
  { id: 'todo-' + nanoid(), label: 'Create a to-do list', done: false },
])

function handleNewTodo(item) {
  toDoItems.value.push({ id: 'todo-' + nanoid(), label: item, done: false })
}

function handleSortTodos(type) {
  switch (type) {
    case 'order':
      toDoItems.value.sort((item1, item2) => (item1.id < item2.id ? -1 : 1))
      break
    case 'name':
      toDoItems.value.sort((item1, item2) => (item1.label < item2.label ? -1 : 1))
      break
    case 'done':
      toDoItems.value.sort((item1, item2) => item1.done - item2.done)
      break
  }
}
</script>

<template>
  <div id="app">
    <h1>To-Do List</h1>
    <TodoForm @updateTodos="handleNewTodo" />
    <ul>
      <li v-for="item in toDoItems" :key="item.id">
        <TodoItem :label="item.label" :id="item.id" :done="item.done" />
      </li>
    </ul>
    <TodoSort @sortTodos="handleSortTodos" />
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
