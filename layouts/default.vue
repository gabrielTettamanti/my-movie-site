<script setup>
const user = useUser();
</script>
<template>
  <div>
    <nav class="nav-bar">
      <NuxtLink class="nav-bar-button" to="/">Home</NuxtLink>
      <NuxtLink class="nav-bar-button" to="/movies">Movies</NuxtLink>
      <NuxtLink class="nav-bar-button" v-if="!user.isLoggedIn" to="/login">Login</NuxtLink>
      <a class="nav-bar-button" href="#" v-else @click.prevent="user.isLoggedIn = false">Logout</a>
    </nav>
    <slot></slot>
  </div>
</template>
<style lang="scss" scoped>
  $background: #0c0c0d;
  $primary-50: #F2FDF9;
  $primary-100: #E6FCF3;
  $primary-200: #BFF6E0;
  $primary-300: #99F1CD;
  $primary-400: #4DE7A8;
  $primary-500: #00DC82;
  $primary-600: #00C675;
  $primary-700: #00844E;
  $primary-800: #00633B;
  $primary-900: #004227;
  
  .nav-bar{
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    margin: 15px auto;
    max-width: 400px;
    .nav-bar-button {
      font-weight: 700;
      text-decoration: none;
      border: solid 2px $primary-800;
      padding: 10px;
      border-radius: 50px;
      text-align: center;
      transition: .5s;
      &:hover {
        border: solid 2px $primary-600;
        background-color: $primary-600;
      }
    }
  }
</style>