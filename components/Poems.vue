<template>
  <form class="form">
    <ul class="form__list">
      <li v-for="(poem, index) in poems" :key="index" class="form__item">
        <label :for="'poem' + (index + 1)" class="form__label">
          <input
            type="radio"
            :id="'poem' + (index + 1)"
            name="poem"
            class="form__radio-input"
          />
          <span class="form__text">{{ "Стих " + (index + 1) }}</span>
        </label>
      </li>
    </ul>
    <button class="form__button" @click="onSubmit">Посмотреть</button>
  </form>
</template>

<script setup>
const poems = ["Стих 1", "Стих 2", "Стих 3"];

const onSubmit = () => {
  console.log("Form submitted!");
};
</script>

<style scoped lang="scss">
.form {
  font-family: Manrope, sans-serif;
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;

  &__list {
    list-style: none;
    padding: 0;
    margin: 0;
  }

  &__radio-input {
    margin-right: 8px;
  }

  &__text {
    font-size: 16px;
  }

  &__label {
    display: flex;
    align-items: center;
    cursor: pointer;
  }

  &__item {
    margin-bottom: 10px;
  }

  &__button {
    background-color: #007bff;
    color: #fff;
    padding: 8px 16px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    margin-left: 10px;

    &:hover {
      background-color: #0056b3;
    }
  }
}
</style>
