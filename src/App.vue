<template>
  <div class="app">
    <Header/>
    <main class="app__main main__wrapper">
      <div class="info">
        <ul class="main__list">
          <item-list
              v-for="(message, index) in messages"
              :key="index"
              :message="message"
              class="main__item"
          >
          </item-list>
        </ul>
      </div>
      <div class="poems">
        <Poems/>
      </div>
    </main>
    <Footer class="app__footer"/>
  </div>
</template>

<script>
import ItemList from "@/components/ItemList.vue";
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";
import Poems from "@/components/Poems.vue";
import axios from "axios";

export default {
  components: {
    ItemList,
    Header,
    Footer,
    Poems,
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
        .then(async (response) => {
          this.messages = response.data.messages;
          this.data = response.data;

          await this.executeActionsWithDelay();
        })
        .catch((error) => {
          console.error(error);
        });
  },
  methods: {
    async executeActionsWithDelay() {
      await this.replaceMessagesWithDelay();
      await this.deleteMessagesWithDelay();
    },
    async replaceMessagesWithDelay() {
      for (const key in this.data.changes.replace.info) {
        const changeInfo = this.data.changes.replace.info[key];
        const indexToReplace = changeInfo.index;
        const newText = changeInfo.text;

        await this.delay(1000);
        this.messages[indexToReplace] = newText;
      }
    },
    async deleteMessagesWithDelay() {
      const deleteIndices = this.data.changes.delete;
      deleteIndices.sort((a, b) => b - a);

      for (const deleteIndex of deleteIndices) {
        await this.delay(1000);
        this.messages.splice(deleteIndex, 1);
      }
    },
    delay(ms) {
      return new Promise((resolve) => setTimeout(resolve, ms));
    },
  },
};
</script>

<style>
@font-face {
  font-display: swap; /* Check https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-display for other options. */
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 400;
  src: url("./fonts/montserrat-v26-latin-regular.woff2") format("woff2"); /* Chrome 36+, Opera 23+, Firefox 39+, Safari 12+, iOS 10+ */
}

* {
  padding: 0;
  margin: 0;
  font-family: "Montserrat", sans-serif;
}

ul {
  list-style: none;
}

.main__wrapper {
  display: flex;
  justify-content: space-between;
  margin: 0 auto;
  padding: 20px 70px;
  min-height: 683px;
}

.app {
  font-family: Arial, sans-serif;
  background-color: #f0f0f0;
}

.info {
  width: 80%;
}

.poems {
  order: 1;
  margin-left: auto;
}
</style>
