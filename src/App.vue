<template>

  <div id="nav">
    <router-link to="/">Главная</router-link> |
    <router-link to="/about">О приложении</router-link>
  </div>
  <router-view />

</template>

<script>

  export default {}

</script>

<style>

  #app {
    font-family: Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }

  #nav {
    padding: 10px;
  }

  #nav a {
    font-weight: bold;
    color: #2c3e50;
  }

  #nav a.router-link-exact-active {
    color: #42b983;
  }

</style>
