<template>
  <button @click="$emit('click')">
    <slot>
      {{ title }}
    </slot>
  </button>
</template>

<script>
export default {
  name: "AppButton",
  props: {
    title: {
      type: String,
      default: null
    }
  }
}
</script>

<style lang="scss" scoped>
  button {
    padding: 20px 40px;
    color: teal;
    cursor: pointer;
    background: white;
    border-radius: 5px;
    border: 1px solid teal;

    transition: all .3s ease;

    &:hover {
      color: white;
      background: teal;
    }
  }
</style>
