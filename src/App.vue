<template>
  <div class="app">
    <Header class="app__header" />
    <main class="app__main main__wrapper">
      <ul class="main__list">
        <item-list
          v-for="(message, index) in messages"
          :key="index"
          :message="message"
          class="main__item"
        >
          <button @click="deleteMessage(index)" class="delete-button">Удалить</button>
        </item-list>
      </ul>
      <button @click="replaceMessages" class="button app__button">Заменить строки</button>
      <button @click="deleteMessage" class="button app__button">Удалить строки</button>
    </main>
    <Footer class="app__footer" />
  </div>
</template>

<script>
import ItemList from "@/components/ItemList.vue";
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";
import axios from "axios";

export default {
  components: {
    ItemList,
    Header,
    Footer,
  },
  data() {
    return {
      messages: [],
      data: null,
    };
  },
  mounted() {
    axios
      .get("http://localhost:8088")
      .then((response) => {
        this.messages = response.data.messages;
        this.data = response.data;
      })
      .catch((error) => {
        console.error(error);
      });
  },
  methods: {
    replaceMessages() {
      for (const key in this.data.changes.replace.info) {
        const changeInfo = this.data.changes.replace.info[key];
        const indexToReplace = changeInfo.index;
        const newText = changeInfo.text;

        this.messages[indexToReplace] = newText;
      }
    },
    deleteMessage() {
      const deleteIndices = this.data.changes.delete; // Массив индексов для удаления
      deleteIndices.sort((a, b) => b - a); // Сортировка индексов в убывающем порядке

      for (const deleteIndex of deleteIndices) {
        this.messages.splice(deleteIndex, 1); // Удаляем один элемент по индексу
      }
    },
  },
};
</script>

<style>
* {
  padding: 0px;
  margin: 0;
}

.main__wrapper {
  margin: 0 auto;
  padding: 20px 70px;
  min-height: 683px;
}

.app {
  font-family: Arial, sans-serif;
  background-color: #f0f0f0;
}

.button {
  background-color: #007bff;
  color: #fff;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
}

.button:hover {
  background-color: #0056b3;
}

.delete-button {
  background-color: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 10px;
  border-radius: 5px;
  cursor: pointer;
}

.delete-button:hover {
  background-color: #ff3333;
}
</style>
