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
</script>
<style scoped lang="scss">
@use "@/assets/scss/fonts" as *;

.footer {
  background-color: #333;
  color: #fff;
  padding: 20px 0;
  text-align: center;

  &__wrapper {
    display: flex;
    justify-content: space-around;
    margin: 0 auto;
    max-width: 1170px;
  }

  &__column {
    text-align: left;

    h3 {
      @include manrope-font(1.9rem, normal);
      margin-bottom: 10px;
    }

    p {
      @include manrope-font(1.1rem, normal);
      margin: 5px 0;
    }

    ul {
      list-style: none;
      padding: 0;

      li {
        margin-bottom: 5px;

        a {
          text-decoration: none;
          color: #fff;

          &:hover {
            text-decoration: underline;
          }
        }
      }
    }
  }
}
</style>