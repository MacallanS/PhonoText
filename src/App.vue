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
        <!-- Передаем текст элемента в компонент ItemList через props -->
      </item-list>
    </ul>
    <footer>
      <!-- Здесь ваш футер -->
    </footer>
  </div>
</template>

<script>
import ItemList from "@/components/ItemList.vue"; // Импортируем компонент ItemList

export default {
  components: {
    ItemList, // Регистрируем компонент ItemList для использования в шаблоне
  },
  data() {
    return {
      items: [
        { name: "Элемент 1", text: "Описание 1" },
        { name: "Элемент 2", text: "Описание 2" },
        { name: "Элемент 3", text: "Описание 3" },
      ], // Массив объектов, содержащий элементы и описания
    };
  },
};
</script>

<style>
/* Здесь можно добавить глобальные стили для вашего приложения */
</style>
