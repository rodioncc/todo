<template>
  <ul class="todo-list-pending">
    <todo
      v-for="(todo, index) in todos"
      :key="index"
      :todo="todo"
      :onCheck="onCheck"
      @delete-todo="deleteTodo"
    />
  </ul>
</template>

<script>
import Todo from "./Todo";

export default {
  name: "TodoListPending",
  components: { Todo },
  props: ["todos", "deleteTodo", "onCheck"]
};
</script>

<style scoped>
.todo-list-pending {
  margin: 0;
  padding: 0;
  border-bottom: 1px solid rgba(0, 0, 0, 0.1);
}
</style>
