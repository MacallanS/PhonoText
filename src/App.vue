<template>
  <div>
    <header>
      <!-- Здесь ваш заголовок -->
    </header>
    <ul>
      <item-list
        v-for="(item, index) in items"
        :key="index"
        :itemName="item.name"
        :itemText="item.text"
      >
      </item-list>
    </ul>
    <footer>
      <!-- Здесь ваш футер -->
    </footer>
  </div>
</template>

<script>
import ItemList from "@/components/ItemList.vue";

export default {
  components: {
    ItemList,
  },
  data() {
    return {
      items: [
        { name: "Элемент 1", text: "Описание 1" },
        { name: "Элемент 2", text: "Описание 2" },
        { name: "Элемент 3", text: "Описание 3" },
      ],
    };
  },
};
</script>

<style>
/* Здесь можно добавить глобальные стили для вашего приложения */
</style>
