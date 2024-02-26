<template>
  <header class="header">
    <div class="header__wrapper">
      <img src="@/assets/logo-4d9aa449.png" alt="" class="header__logo"/>
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
          <Button @click="openLoginModal">Вход</Button>
          <Button @click="openRegisterModal">Регистрация</Button>
        </div>
      </div>
    </div>
  </header>

  <!--модальное окно для регистрации-->
  <Modal v-model="isRegisterModalOpen">
    <template #header>
      <h2>Зарегистрироваться на сайте</h2>
    </template>
    <template #content>
      <Input v-model="loginUsername" id="reg-login" label="Введите логин"/>
      <Input v-model="loginUsername" id="reg-password" label="Введите пароль"/>
      <Input v-model="loginUsername" id="reg-check" label="Повторите пароль"/>

      <Button>
        Зарегистрироваться
      </Button>
    </template>
  </Modal>

  <!--модальное окно для авторизации-->
  <Modal v-model="isLoginModalOpen">
    <template #header>
      <h2>Войти на сайт</h2>
    </template>
    <template #content>
      <Input v-model="loginUsername" id="auth-login" label="Введите логин"/>
      <Input v-model="loginPassword" id="auth-password" label="Введите пароль"/>

      <Button>
        Войти
      </Button>
    </template>
  </Modal>

</template>

<script setup>
import {ref} from 'vue'
import Button from "@/components/Button.vue";
import Modal from "@/components/Modal.vue";
import Input from "@/components/Input.vue";

const isRegisterModalOpen = ref(false)
const regUsername = ref('');
const regPassword = ref('');
const regCheck = ref('');

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
</style>
