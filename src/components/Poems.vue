<template>
  <ul>
    <li>
      <label for="1">
        <input type="radio" id="1" name="poem" />
        Стих 1
      </label>
    </li>
    <li class="poem">
      <label for="2">
        <input type="radio" id="2" name="poem" />
        Стих 2
      </label>
    </li>
    <li>
      <label for="3">
        <input type="radio" id="3" name="poem" />
        Стих 3
      </label>
    </li>
  </ul>
</template>

<script>
export default {
  name: "Poems",
};
</script>

<style scoped>
.poem {
  display: flex;
}
</style>
