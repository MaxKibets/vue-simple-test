<template>
    <header class="header">
        <a href="#" class="header-logo">
            <img src="./assets/logo.png" alt="">
        </a>

        <div v-if='userLoggedIn && userName' class="user-greeting">Hi, {{ userName }}!</div>

        <loginForm v-if='!userLoggedIn' :onLogin='onLogin' />
    </header>
</template>

<script>
import loginForm from "./LoginForm";

export default {
  props: ["userLoggedIn", "userName", "onLogin"],
  components: {
    loginForm
  }
};
</script>

<style>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 5px 30px;
  border-bottom: 1px solid var(--main-border-green);
  background-color: var(--main-green);
  box-shadow: var(--main-shadow);
}
.header-logo {
  max-width: 35px;
  max-height: 35px;
  padding: 10px;
  border-radius: 50%;
  border: 2px solid #536777;
  background-color: #fff;
  animation: flashingLogo 700ms infinite alternate-reverse ease;
  animation-fill-mode: both;
}
.user-greeting {
  font-weight: bold;
}
@keyframes flashingLogo {
  0% {
    background-color: rgba(255, 255, 255, 0.4);
    transform: scale(0.95);
  }
  100% {
    background-color: rgba(255, 255, 255, 1);
    transform: scale(1);
  }
}
.header-logo img {
  display: block;
  max-width: 100%;
  max-height: 100%;
  transition: transform 700ms ease;
}
.header-logo:hover img {
  transform: rotateY(360deg);
}
</style>

