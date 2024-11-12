<script setup>
const props = defineProps({
  label: { required: true, type: String },
  id: { required: true, type: String },
  done: { default: false, type: Boolean },
})

const isDone = props.done
</script>

<template>
  <input type="checkbox" :id="id" :checked="isDone" />
  <label :for="id">{{ label }}</label>
</template>

<style lang="css" scoped>
input + label {
  margin-left: 0.5em;
}
</style>
