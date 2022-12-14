<template>
  <div :class="['todo', { 'stroke':todo.completed }]">
    <div class="todo__id">
      {{ todo.id }}
    </div>
    <div class="todo__title">
      {{ todo.title }}
    </div>
    <input
        type="checkbox"
        :checked="todo.completed"
        @click="todo.completed = !todo.completed"
    />
    <close-button @click="$emit('delete-todo', todo.id)" title="X" />
  </div>
</template>

<script>
  import AppButton from "@/components/ui/AppButton.vue";
  import CloseButton from "@/components/ui/CloseButton.vue";
  export default {
    name: 'TodoListItem',
    components: { CloseButton, AppButton },
    props: {
      todo: {
        type: Object,
        required: true
      }
    }
  }
</script>

<style lang="scss" scoped>
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

  .stroke .todo__title{
    text-decoration: line-through;
  }
</style>
