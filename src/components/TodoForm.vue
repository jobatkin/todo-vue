<script setup>
import { ref, defineEmits } from 'vue'

const newTodo = ref('')
const emit = defineEmits(['updateTodos'])

function handleSubmit() {
  emit('updateTodos', newTodo.value)
}
</script>

<template>
  <form @submit.prevent="handleSubmit" class="module">
    <label for="new-todo-input"> What needs to be done? </label>
    <input
      type="text"
      id="new-todo-input"
      v-model.lazy.trim="newTodo"
      name="new-todo"
      autocomplete="off"
    />
    <button type="submit">Add</button>
  </form>
</template>
