<template>
  <input
      :type="type"
      :value="value"
      placeholder="Купить хлеб"
      @input="$emit('input', $event.target.value)"/>
</template>

<script>
  export default {
    name: 'AppTextField',
    props: {
      type: {
        Type: String,
        default: 'text'
      },
      value: {
        validate(value) {
          return typeof value === String || value === null
        }
      }
    }
  }
</script>

<style lang="scss" scoped>
  input {
    padding: 18px 5px;
  }
</style>
