<template>
  <div v-if="todos.length" class="todo-list">
    <todo-list-pending
      :todos="pendingTasks"
      :deleteTodo="deleteTodo"
      :onCheck="onCheck"
    />
    <todo-list-completed
      :todos="completedTasks"
      :deleteTodo="deleteTodo"
      :onCheck="onCheck"
    />
  </div>
  <no-todos v-else />
</template>

<script>
import TodoListPending from "./TodoListPending";
import TodoListCompleted from "./TodoListCompleted";
import NoTodos from "./NoTodos";

export default {
  name: "TodoList",
  components: { TodoListPending, TodoListCompleted, NoTodos },
  props: ["todos", "pendingTasks", "completedTasks", "deleteTodo", "onCheck"]
};
</script>

<style scoped lang="scss">
.todo-list {
  overflow: auto;
}
</style>
