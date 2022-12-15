<template>
  <div :class="['dialog', { 'active':value }]" @click="$emit('input',false)">
    <div class="dialog__wrapper" @click.stop>
      <button-close class="dialog__close" @click="$emit('input',false)" />
      <slot />
    </div>
  </div>
</template>

<script>
  import ButtonClose from "@/components/ui/ButtonClose.vue";
  export default {
    name: 'AppDialog',
    components: { ButtonClose },
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
