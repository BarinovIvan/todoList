<template>
  <div class="container">
    <TodoListItem
        v-for="todo in todoList"
        :key="todo.id"
        :todo="todo"
        @change-completion="changeCompletion($event)"
        @delete-todo="deleteTodo($event)"
    />
    <div
        class="todo__message"
        v-if="this.todoList != 0"
    >
      <p>Список задач</p>
    </div>
    <div class="todo__message"
         v-else
    >
      <p>Список задач пуст</p>
      <a href="/">+Добавить</a>
    </div>
  </div>
</template>

<script>
import TodoListItem from "./TodoListItem.vue";

export default {
  name: 'TodoList',
  components: {TodoListItem},
  data() {
    return {
      todoList: [
        {id: 1, title: 'Купить орехов', completed: false},
        {id: 2, title: 'Купить кастрюлю', completed: false},
        {id: 3, title: 'Купить сковороду', completed: false},
        {id: 4, title: 'Купить молока', completed: false},
        {id: 5, title: 'Купить шоколода', completed: false},
        {id: 6, title: 'Купить полотенце', completed: false}
      ]
    }
  },
  methods: {
    changeCompletion(todoId) {
      let todoFound = this.todoList.find(todo => todo.id === todoId)
      todoFound.completed = !todoFound.completed
    },
    deleteTodo(todoId) {
      this.todoList = this.todoList.filter(todo => todo.id !== todoId)
    }
  }
}
</script>

<style lang="scss">
.todo__message {
  text-align: center;
  margin: 30px auto;

  p {
    margin-bottom: 5px;
  }
}
</style>
