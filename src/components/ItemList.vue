<template>
  <li class="item-list">
    <h2 class="item-list__title">
      {{ itemName }}
    </h2>
    <p class="item-list__description">
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
.item-list {
  background-color: #f0f0f0;
  border: 1px solid #ddd;
  padding: 10px;
  margin-bottom: 10px;
  border-radius: 5px;
  list-style: none;
}

.item-list__title {
  font-size: 1.2rem;
  margin: 0;
}

.item-list__description {
  font-size: 0.9rem;
  margin: 10px 0;
  color: #555;
}
</style>
