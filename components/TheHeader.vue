<template>
  <header class="header">
    <div class="header__wrapper">
      <a href="/"><img src="@/assets/images/logo.png" alt="" class="header__logo" /></a>
      <div class="header__info">
        <nav class="header__nav">
          <ul>
            <li><a href="/" class="header__nav-link">Главная</a></li>
            <li><a href="/about" class="header__nav-link">О нас</a></li>
            <li><a href="/contact" class="header__nav-link">Контакты</a></li>
          </ul>
        </nav>
        <div class="header__buttons">
          <button class="button button--login" @click="openLoginModal">Вход</button>
          <button class="button button--register" @click="openRegisterModal">Регистрация</button>
        </div>
      </div>
    </div>
  </header>
  <ModalWindow v-model="isRegisterModalOpen">
    <template #header>
      <h2>Зарегистрироваться на сайте</h2>
    </template>
    <template #content>
      <StyledInput v-model="regUsername" id="reg-login" label="Введите логин"/>
      <StyledInput v-model="regPassword" id="reg-password" label="Введите пароль"/>
      <StyledInput v-model="regCheck" id="reg-check" label="Повторите пароль"/>

      <button class="button">
        Зарегистрироваться
      </button>
    </template>
  </ModalWindow>
  <ModalWindow v-model="isLoginModalOpen">
    <template #header>
      <h2>Войти на сайт</h2>
    </template>
    <template #content>
      <StyledInput v-model="loginUsername" id="auth-login" label="Введите логин"/>
      <StyledInput v-model="loginPassword" id="auth-password" label="Введите пароль"/>

      <button class="button">
        Войти
      </button>
    </template>
  </ModalWindow>
</template>

<script setup>
import { ref } from 'vue'
import StyledInput from '~/components/StyledInput.vue'

const isRegisterModalOpen = ref(false)
const regUsername = ref('')
const regPassword = ref('')
const regCheck = ref('')

const isLoginModalOpen = ref(false)
const loginUsername = ref('')
const loginPassword = ref('')

const openRegisterModal = () => {
  isRegisterModalOpen.value = true
}

const openLoginModal = () => {
  isLoginModalOpen.value = true
}
</script>

<style lang="scss">
@use "@/assets/scss/fonts" as *;

.header {
  background-color: #333;
  color: #fff;
  padding: 10px;
  text-align: center;

  &__wrapper {
    display: flex;
    justify-content: space-around;
    margin: 0 auto;
    max-width: 1170px;
  }

  &__info {
    display: flex;
    justify-content: space-around;
    align-items: center;
  }

  &__nav {
    ul {
      list-style: none;
      padding: 0;

      li {
        display: inline;
        margin-right: 20px;

        .header__nav-link {
          @include manrope-font(16px, bold);
          text-decoration: none;
          color: #fff;
        }
      }
    }
  }

  &__buttons {
    display: flex;
    text-align: right;
  }

  .button {
    & {
      @include manrope-font(14px, normal);
      padding: 8px 16px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      margin-left: 10px;
    }

    &--login {
      background-color: #007bff;
      color: #fff;

      &:hover {
        background-color: #0056b3;
      }
    }

    &--register {
      background-color: #28a745;
      color: #fff;

      &:hover {
        background-color: #218838;
      }
    }
  }
}
</style>
