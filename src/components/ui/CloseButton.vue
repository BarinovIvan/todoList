<template>
  <button @click="$emit('click')">
    Х
  </button>
</template>

<script>
export default {
  name: "CloseButton"
}
</script>

<style lang="scss" scoped>
  button {
    width: 20px;
    height: 20px;
    color: white;
    background: red;
    cursor: pointer;
    border-radius: 2.5px;
    border: 1px solid transparent;

    transition: all .3s ease;

    &:hover {
      color: red;
      background: white;
      border: 1px solid red;
    }
  }

</style>
