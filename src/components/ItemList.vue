<template>
  <li class="item-list">
    <p class="item-list__description">
      {{ message }}
    </p>
  </li>
</template>

<script>
export default {
  props: {
    message: String,
  },
};
</script>

<style scoped>
.item-list {
  background-color: #fff;
  border: 1px solid #ddd;
  padding: 10px;
  margin-bottom: 10px;
  border-radius: 5px;
  list-style: none;
}

.item-list__description {
  font-size: 18px;
  margin: 10px 0;
  color: #333;
}
</style>
