<template>
  <li>
    <!-- Отображаем текст элемента, переданный через props -->
    <h2>
      {{ itemName }}
    </h2>
    <p>
      {{ itemText }}
    </p>
  </li>
</template>

<script>
export default {
  props: {
    itemName: String, // Принимаем текст элемента через props
    itemText: String, // Принимаем текст элемента через props
  },
};
</script>

<style scoped>
/* Здесь можно добавить стили для компонента ItemList */
</style>
