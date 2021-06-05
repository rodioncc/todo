<template>
  <form class="add-todo">
    <button @click.prevent="addTodo" class="add-todo-button" />
    <input
      autoFocus
      type="text"
      v-model="text"
      class="add-todo-input"
      placeholder="Add Todo"
    />
  </form>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      text: ""
    };
  },
  methods: {
    addTodo() {
      const text = this.text.trim();
      if (text.length > 0) {
        this.$emit("add-todo", text);
        this.text = "";
      }
    }
  }
};
</script>

<style scoped lang="scss">
.add-todo {
  display: flex;
  align-items: center;
  padding: 0 18px;
  button {
    margin-right: 10px;
  }
  input {
    flex: 1 0 auto;
  }
  &-button {
    border: 0;
    background: url("../assets/icons/add-icon.svg") center no-repeat;
    background-size: contain;
    padding: 0;
    cursor: pointer;
    border-radius: 4px;
    transition: 300ms;
    height: 18px;
    width: 18px;
    &:focus {
      outline: none;
    }
    &:hover {
      background-color: #e0e0e0;
    }
  }
  &-input {
    border: 0;
    border-bottom: 1px solid transparent;
    transition: 200ms;
    font-size: 13px;
    color: #444;
    line-height: 1.8;
    &:focus {
      outline: none;
      border-color: #afb1b0;
    }
    &::placeholder {
      color: #afb1b0;
      font-size: 13px;
    }
  }
}
</style>
