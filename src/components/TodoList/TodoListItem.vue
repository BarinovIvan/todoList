<template>
  <div class="todo">
    <div class="todo__id">
      {{ todo.id }}
    </div>
    <div :class="['todo__title', { 'stroke':todo.completed }]">
      {{ todo.title }}
    </div>
    <input
        type="checkbox"
        :checked="todo.completed"
        @click="todo.completed = !todo.completed"
    />
    <button @click="$emit('delete-todo', todo.id)">X</button>
  </div>
</template>

<script>
  export default {
    name: 'TodoListItem',
    props: {
      todo: {
        type: Object,
        required: true
      }
    }
  }
</script>

<style scoped lang="scss">
.todo {
  position: relative;
  display: flex;
  align-items: center;
  margin-top: 20px;
  padding: 20px;
  border-radius: 25px;
  box-shadow: 0 0 10px #646464;
  border: 1px solid transparent;

  transition: border .3s;

  &:hover {
    border: 1px solid black;
  }

  &__id {
    flex-basis: 30px;
  }

  &__title {
    flex-basis: 100%;
  }
}

input[type="checkbox"] {
  height: 20px;
  flex-basis: 60px;
  cursor: pointer;
}

button {
  background: #ff3737;
  padding: 5px 10px;
  border-radius: 15px;
  cursor: pointer;
  color: white;
}

.stroke{
  text-decoration: line-through;
}

</style>
