<template>
  <form class="form" @submit.prevent="onSubmit">
    <ul class="form__list">
      <li class="form__item">
        <label for="1" class="form__label">
          <input type="radio" id="1" name="poem" class="form__radio-input" />
          <img src="" alt="" class="form__image" />
          <span class="form__text">Стих 1</span>
        </label>
      </li>
      <li class="form__item">
        <label for="2" class="form__label">
          <input type="radio" id="2" name="poem" class="form__radio-input" />
          <img src="" alt="" class="form__image" />
          <span class="form__text">Стих 2</span>
        </label>
      </li>
      <li class="form__item">
        <label for="3" class="form__label">
          <input type="radio" id="3" name="poem" class="form__radio-input" />
          <img src="" alt="" class="form__image" />
          <span class="form__text">Стих 3</span>
        </label>
      </li>
    </ul>
    <button class="btn form__button" type="submit">Посмотреть</button>
  </form>
</template>

<script>
import axios from "axios";
export default {
  name: "Poems",
  data() {
    return {
      selectedPoem: null,
    };
  },
  methods: {
    onSubmit() {
      const selectedData = this.selectedData;
      this.sendDataToServer(selectedData);
    },
    async sendDataToServer(selectedData) {
      try {
        const response = await axios.post("http://localhost:8088/sendData", {
          selectedData,
        });
        console.log("Данные успешно отправлены на сервер", response.data);
      } catch (error) {
        console.error("Ошибка при отправке данных на сервер", error);
      }
    },
  },
};
</script>

<style scoped>
.form {
  font-family: Arial, sans-serif;
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.form__list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.form__item {
  margin-bottom: 10px;
}

.form__label {
  display: flex;
  align-items: center;
  cursor: pointer;
}

.form__radio-input {
  margin-right: 8px;
}

.form__image {
  width: 30px;
  height: 30px;
  margin-right: 8px;
}

.form__text {
  font-size: 16px;
}

.form__button {
  padding: 10px 20px;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 3px;
  cursor: pointer;
  font-size: 16px;
}

.form__button:hover {
  background-color: #0056b3;
}
</style>
