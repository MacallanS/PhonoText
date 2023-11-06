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
          :class="{
            'animate-fade': index === messageIndex,
            'animate-fade-in': index !== messageIndex,
          }"
        ></item-list>
      </ul>
      <button @click="replaceMessage" class="button app__button">Заменить строку</button>
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
      messageIndex: -1, // Индекс сообщения, которое будет заменено
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
    replaceMessage() {
      const indexToReplace = this.data.replace.index;
      const newText = this.data.replace.text;

      this.messageIndex = indexToReplace;

      setTimeout(() => {
        this.messages[indexToReplace] = newText;
        this.messageIndex = -1;
      }, 1000);
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

.animate-fade {
  transition: opacity 1s;
  opacity: 0;
}

.animate-fade-in {
  transition: opacity 1s;
  opacity: 1;
}

@keyframes fade {
  0% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
}
</style>
