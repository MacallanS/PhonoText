<template>
  <footer class="footer">
    <div class="footer__wrapper">
      <div class="footer__column">
        <h3>О нас</h3>
        <p>Наша компания предоставляет...</p>
      </div>
      <div class="footer__column">
        <h3>Свяжитесь с нами</h3>
        <p>Email: info@example.com</p>
        <p>Телефон: +1 (123) 456-7890</p>
      </div>
      <div class="footer__column">
        <h3>Полезные ссылки</h3>
        <ul>
          <li><a href="/terms">Условия использования</a></li>
          <li><a href="/privacy">Политика конфиденциальности</a></li>
        </ul>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "Footer",
};
</script>

<style scoped>
.footer {
  background-color: #333;
  color: #fff;
  padding: 20px 0;
  text-align: center;
}

.footer__wrapper {
  display: flex;
  justify-content: space-around;
  margin: 0 auto;
  max-width: 1170px;
}

.footer__column {
  text-align: left;
}

.footer__column h3 {
  font-size: 1.2rem;
  margin-bottom: 10px;
}

.footer__column p {
  font-size: 0.9rem;
  margin: 5px 0;
}

.footer__column ul {
  list-style: none;
  padding: 0;
}

.footer__column li {
  margin-bottom: 5px;
}

.footer__column a {
  text-decoration: none;
  color: #fff;
}

.footer__column a:hover {
  text-decoration: underline;
}
</style>
