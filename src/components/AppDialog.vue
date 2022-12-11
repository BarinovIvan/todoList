<template>
  <div :class = "['dialog',{ 'active':value }]" @click="$emit('input',false)">
    <div class="dialog__wrapper" @click.stop>
      <button class="dialog__close" @click="$emit('input',false)">
        X
      </button>
      <slot />
    </div>
  </div>
</template>

<script>
  export default {
    name: 'AppDialog',
    props: {
      value: {
        type: Boolean,
        default: false
      }
    }
  }
</script>

<style lang="scss" scoped>
  .dialog {
    position: absolute;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.3);
    backdrop-filter: blur(4px);
    bottom: 0;
    right: 0;
    left: 0;
    top: 0;
    display: none;
    align-items: center;
    text-align: center;

    &__wrapper {
      position: relative;
      padding: 30px 60px;
      margin: 0 auto;
      width: 300px;
      background: white;
      border-radius: 5px;
    }

    &__close {
      position: absolute;
      padding: 4px 8px;
      right: 5px;
      top: 5px;
      background: rgba(89, 68, 68, 0.2);
      border-radius: 0;
    }
  }

  .active {
    display: flex;
  }
</style>
