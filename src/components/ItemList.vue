<template>
  <li>
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
    itemName: String,
    itemText: String,
  },
};
</script>

<style scoped>
/* Здесь можно добавить стили для компонента ItemList */
</style>
