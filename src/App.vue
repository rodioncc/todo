<template>
  <div class="todo-app">
    <title-top />
    <add-todo @add-todo="addTodo" />
    <todo-list
      :todos="todos"
      :addTodo="addTodo"
      :completedTasks="completedTasks"
      :pendingTasks="pendingTasks"
      :deleteTodo="deleteTodo"
      :onCheck="onCheck"
    />
    <info :completedTasks="completedTasks" :pendingTasks="pendingTasks" />
  </div>
</template>

<script>
import TitleTop from "./components/Title";
import AddTodo from "./components/AddTodo";
import TodoList from "./components/TodoList";
import Info from "./components/Info";

export default {
  name: "App",
  components: {
    TitleTop,
    AddTodo,
    TodoList,
    Info
  },
  data() {
    return {
      todos: []
    };
  },
  mounted() {
    if (localStorage.todos) {
      console.log(localStorage.todos);
      this.todos = JSON.parse(localStorage.todos);
    }
  },
  watch: {
    todos(newTodos) {
      console.log(newTodos);
      localStorage.todos = JSON.stringify(newTodos);
    }
  },
  computed: {
    completedTasks() {
      return this.todos.filter(todo => !!todo.done);
    },
    pendingTasks() {
      return this.todos.filter(todo => !todo.done);
    }
  },
  methods: {
    addTodo(text) {
      this.todos.push({
        text,
        done: false
      });
    },
    deleteTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    },
    onCheck(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.$set(this.todos, todoIndex, {
        ...this.todos[todoIndex],
        done: !this.todos[todoIndex].done
      });
    }
  }
};
</script>

<style lang="scss">
$fonts_url: "./assets/fonts/";
$family: "Roboto";

$light: $fonts_url + "Roboto-Light.ttf";
$regular: $fonts_url + "Roboto-Regular.ttf";
$bold: $fonts_url + "Roboto-Bold.ttf";

@font-face {
  font-family: $family;
  src: url($light);
  font-weight: 300;
}

@font-face {
  font-family: $family;
  src: url($regular);
  font-weight: 400;
}

@font-face {
  font-family: $family;
  src: url($bold);
  font-weight: 700;
}

html,
body {
  height: 100%;
}

body {
  background: #4fc08d;
  padding: 0;
  margin: auto;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  font-family: $family, -apple-system, BlinkMacSystemFont, "Segoe UI", "Oxygen",
    "Ubuntu", "Cantarell", "Fira Sans", "Droid Sans", "Helvetica Neue",
    sans-serif;
}

@media (max-width: 420px) {
  body {
    background: #fff;
  }
}

.todo-app {
  padding: 0 0 50px;
  background: #fff;
  width: 300px;
  height: 500px;
  max-width: 100%;
  box-shadow: 0 4px 16px 0 rgba(0, 0, 0, 0.35);
  position: relative;
  display: flex;
  flex-direction: column;
  border-radius: 6px;
  overflow: hidden;
  form {
    margin-bottom: 30px;
  }

  @media (max-width: 420px) {
    width: 100%;
    height: 100%;
  }
}
</style>
