<template>
  <div class="todo-delete">
    <h3 class="todo-delete__title">Удалить элемент?</h3>
    <app-button @click="$emit('clickDeleteTodo')">Да</app-button>
    <app-button @click="$emit('clickCloseTodo')">Нет</app-button>
  </div>
</template>

<script>
import AppButton from "@/components/ui/AppButton.vue";
export default {
  name: "TodoDeleteForm",
  components: { AppButton }
}
</script>

<style lang="scss" scoped>
.todo-delete {
  &__title {
    margin-bottom: 20px;
  }
  button:not(:last-child) {
    margin-right: 20px;
  }
}
</style>
