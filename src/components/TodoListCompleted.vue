<template>
  <ul class="todo-list-completed">
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
  name: "TodoListCompleted",
  components: { Todo },
  props: ["todos", "deleteTodo", "onCheck"]
};
</script>

<style scoped>
.todo-list-completed {
  margin: 0;
  padding: 0;
}
</style>
