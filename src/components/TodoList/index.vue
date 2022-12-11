<template>
  <div class="container">
    <todo-list-item
        v-for="todo in todoList"
        :key="todo.id"
        :todo="todo"
        @delete-todo="deleteTodoWarning($event)"
    />
    <div v-if="this.todoList !== 0" class="todo__message">
      <p>Список задач</p>
    </div>
    <div v-else class="todo__message">
      <p>Список задач пуст</p>
      <button>+Добавить</button>
    </div>
    <app-dialog v-model="dialogIsShown">
      <div class="todo-delete">
        <h3 class="todo-delete__title">Удалить элемент?</h3>
        <button @click="deleteTodo()">Да</button>
        <button @click="closeTodoDialog()">Нет</button>
      </div>
    </app-dialog>
  </div>
</template>

<script>
  import TodoListItem from "./TodoListItem.vue";
  import AppDialog from "@/components/AppDialog.vue";

  export default {
    name: 'TodoList',
    components: {AppDialog, TodoListItem},
    data() {
      return {
        dialogIsShown: false,
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
      deleteTodoWarning(todoId) {
        this.showTodoDialog()
        this.currentTodo = todoId
      },
      deleteTodo() {
        this.todoList = this.todoList.filter(item => item.id !== this.currentTodo)
        this.closeTodoDialog()
      }
    }
  }
</script>

<style lang="scss" scoped>
  .todo__message {
    text-align: center;
    margin: 30px auto;

    p {
      margin-bottom: 5px;
    }
  }

  .todo-delete {

    &__title {
      margin-bottom: 20px;
    }

    button:not(:last-child) {
      margin-right: 20px;
    }
  }

  .todo__message button{
    margin-top: 10px;
    text-transform: uppercase;
  }
</style>
