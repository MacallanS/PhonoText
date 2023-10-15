<template>
  <div>
    <Header />
    <main class="main__wrapper">
      <ul>
        <item-list
          v-for="(item, index) in items"
          :key="index"
          :itemName="item.name"
          :itemText="item.text"
        >
        </item-list>
      </ul>
    </main>
    <Footer />
  </div>
</template>

<script>
import ItemList from "@/components/ItemList.vue";
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";

export default {
  components: {
    ItemList,
    Header,
    Footer,
  },
  data() {
    return {
      items: [
        { name: "Текс", text: "Вью" },
        { name: "Элемент 2", text: "Описание 2" },
        { name: "Элемент 3", text: "Описание 3" },
        { name: "Элемент 3", text: "Описание 3" },
        { name: "Элемент 3", text: "Описание 3" },
        { name: "Элемент 3", text: "Описание 3" },
        { name: "Элемент 3", text: "Описание 3" },
        { name: "Элемент 3", text: "Описание 3" },
        { name: "Элемент 3", text: "Описание 3" },
        { name: "Элемент 3", text: "Описание 3" },
        { name: "Элемент 3", text: "Описание 3" },
        { name: "Элемент 3", text: "Описание 3" },
        { name: "Элемент 3", text: "Описание 3" },
        { name: "Элемент 3", text: "Описание 3" },
        { name: "Элемент 3", text: "Описание 3" },
        { name: "Элемент 3", text: "Описание 3" },
        { name: "Элемент 3", text: "Описание 3" },
      ],
    };
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

.main__wrapper {
  margin: 0 auto;
  max-width: 1170px;
}
</style>
