<template>
  <header class="header">
    <div class="header__wrapper">
      <img src="@/assets/logo-4d9aa449.png" alt="" class="header__logo" />
      <div class="header__info">
        <nav class="header__nav">
          <ul>
            <li><a href="/">Главная</a></li>
            <li><a href="/about">О нас</a></li>
            <li><a href="/services">Услуги</a></li>
            <li><a href="/contact">Контакты</a></li>
          </ul>
        </nav>
        <div class="header__buttons">
          <button class="header__button">Вход</button>
          <button class="header__button">Welcome to the club</button>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style scoped>
.header {
  background-color: #333;
  color: #fff;
  padding: 10px;
  text-align: center;
}

.header__wrapper {
  display: flex;
  justify-content: space-around;
  margin: 0 auto;
  max-width: 1170px;
}

.header__info {
  display: flex;
  justify-content: space-around;
  align-items: center;
}
.header__nav ul {
  list-style: none;
  padding: 0;
}

.header__nav li {
  display: inline;
  margin-right: 20px;
}

.header__nav a {
  text-decoration: none;
  color: #fff;
  font-weight: bold;
}

.header__buttons {
  text-align: right;
}

.header__button {
  background-color: #007bff;
  color: #fff;
  padding: 8px 16px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin-left: 10px;
}

.header__button:hover {
  background-color: #0056b3;
}
</style>
