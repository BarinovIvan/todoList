<template>
  <div class="todo-create">
    <h3 class="todo-create__title">Создать элемент?</h3>
    <app-text-field
        v-model="inputTodoTitle"
        class="todo-create__text-field"
    />
    <div class="todo-create__button-wrapper">
      <app-button @click="addNewTodo()">Создать</app-button>
      <app-button @click="$emit('clickCloseTodo')">Отмена</app-button>
    </div>
  </div>
</template>

<script>
import AppButton from "@/components/ui/AppButton.vue";
import AppTextField from "@/components/ui/AppTextField.vue";

export default {
  name: "TodoCreateForm",
  components: { AppButton, AppTextField },
  data() {
    return {
      inputTodoTitle: ''
    }
  },
  methods: {

    addNewTodo() {
      if(this.inputTodoTitle == '') {
        return
      }
      this.$emit('added-todo',{
        id: Date.now(),
        title: this.inputTodoTitle,
        completed: false
      })
      this.inputTodoTitle = ''
    }
  }
}
</script>

<style lang="scss" scoped>
.todo-create {
  &__title {
    margin-bottom: 20px;
  }

  &__text-field {
    width: 80%;
  }

  &__button-wrapper {
    display: flex;
    justify-content: center;
    margin-top: 20px;

    button:not(:last-child) {
      margin-right: 20px;
    }
  }
}
</style>
