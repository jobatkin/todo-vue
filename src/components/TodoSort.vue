<script setup>
import { ref, defineEmits } from 'vue'

const todoSort = ref('')
const emit = defineEmits(['sortTodos'])

function handleChange() {
  emit('sortTodos', todoSort.value)
}
</script>

<template>
  <label
    >Sort by:
    <select v-model="todoSort" @change="handleChange">
      <option value="order">Order</option>
      <option value="name">Name</option>
      <option value="done">Completed</option>
    </select></label
  >
</template>
