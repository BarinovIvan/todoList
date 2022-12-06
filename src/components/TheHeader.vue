<template>
  <div class="header">
    <div class="container">
      <div class="header__logo">LOGO</div>
      <nav>
        <a href="/">List Todos</a>
        <a href="/">Create todo</a>
      </nav>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'TheHeader',
  }
</script>

<style scoped lang="scss">
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