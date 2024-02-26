<template>
  <div class="input-component">
    <label :for="id">{{ label }}</label>
    <input :id="id" :value="modelValue" @input="$emit('update:modelValue', $event.target.value)" />
  </div>
</template>

<script>
export default {
  name: "Input",
  props: {
    id: String,
    label: String,
    modelValue: String
  },
  emits: ['update:modelValue']
}
</script>

<style scoped>
.input-component {
  margin-bottom: 1rem;
}

.input-component label {
  display: block;
  margin-bottom: 0.5rem;
}

.input-component input {
  width: 100%;
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 4px;
}
</style>
