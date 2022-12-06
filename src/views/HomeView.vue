<template>
  <div>
    <the-header/>
    <todo-list/>
  </div>
</template>

<script>
import TodoList from "@/components/TodoList/index.vue";
import TheHeader from "@/components/TheHeader.vue";
export default {
  name: 'HomeView',
  components: {
    TodoList,
    TheHeader
  }
}
</script>
