<template>
  <div class="container">
    <div class="todo__title">
      <h1>Todo List</h1>
      <app-button @click="openTodoCreateDialog()">+Добавить</app-button>
    </div>
    <todo-list-item
        v-for="todo in todoList"
        :key="todo.id"
        :todo="todo"
        @delete-todo="openTodoDeleteDialog($event)"
    />
    <div v-if="this.todoList.length === 0" class="todo__message">
      <p>Список задач пуст</p>
    </div>
    <app-dialog v-model="dialogIsShown" class="todo__dialog">
      <todo-delete-form
          v-if="DeleteFormIsShown"
          @clickCloseTodo="closeTodoDialog()"
          @clickDeleteTodo="deleteTodo()"
      />
      <todo-create-form
          v-else
          @clickCloseTodo="closeTodoDialog()"
          @clickDeleteTodo="createTodo()"
          @added-todo="createTodo($event)"
      />
    </app-dialog>
  </div>
</template>

<script>
  import TodoListItem from "./TodoListItem.vue";
  import AppDialog from "@/components/ui/AppDialog.vue";
  import TodoDeleteForm from "@/components/ui/TodoDeleteForm.vue";
  import AppButton from "@/components/ui/AppButton.vue";
  import TodoCreateForm from "@/components/ui/TodoCreateForm.vue";
  import dialogNames from "@/components/constants/dialog-names.js"

  export default {
    name: 'TodoList',
    components: { TodoCreateForm, AppButton, TodoDeleteForm, AppDialog, TodoListItem },
    data() {
      return {
        dialogIsShown: false,
        dialogName: dialogNames.CREATE,
        todoList: [
          { id: 1, title: 'Купить орехов', completed: false },
          { id: 2, title: 'Купить кастрюлю', completed: false },
          { id: 3, title: 'Купить сковороду', completed: false },
          { id: 4, title: 'Купить молока', completed: false },
          { id: 5, title: 'Купить шоколода', completed: false },
          { id: 6, title: 'Купить полотенце', completed: false }
        ],
        currentTodo: null
      }
    },
    methods: {
      closeTodoDialog() {
        this.dialogIsShown = false
      },
      showTodoDialog() {
        this.dialogIsShown = true
      },
      openTodoCreateDialog() {
        this.dialogName = dialogNames.CREATE
        this.showTodoDialog()
      },
      createTodo(newTodo) {
        newTodo.id = this.todoList.length + 1
        this.todoList.push(newTodo)
        this.closeTodoDialog()
      },
      openTodoDeleteDialog(todoId) {
        this.dialogName = dialogNames.DELETE
        this.showTodoDialog()
        this.currentTodo = todoId
      },
      deleteTodo(todoId) {
        this.todoList = this.todoList.filter(item => item.id !== this.currentTodo)
        this.closeTodoDialog()
      }
    },
    computed: {
      DeleteFormIsShown() {
        if (this.dialogName == dialogNames.DELETE) return true
      }
    }
  }
</script>

<style lang="scss" scoped>
.todo{
  &__title {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 10px;
  }

  &__message {
    text-align: center;
    margin: 30px auto;
  }

  &__dialog {
    position: absolute;
    bottom: 0;
    right: 0;
    left: 0;
    top: 0;
  }
}
</style>
