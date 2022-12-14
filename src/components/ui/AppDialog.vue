<template>
  <div :class="['dialog', { 'active':value }]" @click="$emit('input',false)">
    <div class="dialog__wrapper" @click.stop>
      <close-button class="dialog__close" @click="$emit('input',false)" label="X" />
      <slot />
    </div>
  </div>
</template>

<script>
  import CloseButton from "@/components/ui/CloseButton.vue";
  export default {
    name: 'AppDialog',
    components: { CloseButton },
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
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.3);
    backdrop-filter: blur(4px);
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
      right: 5px;
      top: 5px;
    }

    &.active {
      display: flex;
    }
  }
</style>
