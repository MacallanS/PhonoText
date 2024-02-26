<template>
  <button class="button">
    <slot></slot>
  </button>
</template>

<script setup>
</script>

<style scoped>
.button {
  background-color: #007bff;
  color: #fff;
  padding: 8px 16px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin-left: 10px;
}

.button:hover {
  background-color: #0056b3;
}
</style>