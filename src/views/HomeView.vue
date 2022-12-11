<template>
  <div>
    <todo-list />
  </div>
</template>

<script>
  import TodoList from "@/components/TodoList/index.vue";
  import AppDialog from "@/components/AppDialog";

  export default {
    name: 'HomeView',
    components: {
      AppDialog,
      TodoList
    }
  }
</script>
