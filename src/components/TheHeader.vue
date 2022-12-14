<template>
  <div class="header">
    <div class="container">
      <router-link to="/" class="header__logo">LOGO</router-link>
      <nav>
        <router-link to="/">Todos</router-link>
        <router-link to="/contacts-list">Contact us</router-link>
      </nav>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'TheHeader',
  }
</script>

<style lang="scss" scoped>
  .header {
    color: white;
    background: black;

    .container {
      padding: 20px;
      display: flex;
      justify-content: space-between;
    }
  }

  nav > *:not(:last-child) {
    margin-right: 20px;
  }

  a {
    color: white;
  }
</style>
