<template>
  <li :class="['todo', { done: todo.done }]">
    <checkbox :todo="todo" @on-check="onCheck" />
    <input type="text" v-model="todo.text" />
    <button class="remove-btn" @click="$emit('delete-todo', todo)" />
  </li>
</template>

<script>
import Checkbox from "./Checkbox";
export default {
  name: "Todo",
  components: { Checkbox },
  props: ["todo", "onCheck"]
};
</script>

<style scoped lang="scss">
.todo {
  list-style-type: none;
  padding: 20px 18px;
  display: flex;
  align-items: center;
  position: relative;
  button {
    margin-right: 10px;
  }
  .remove-btn {
    position: absolute;
    right: 20px;
    top: 0;
    bottom: 0;
    margin: auto;
    opacity: 0;
    transition: 300ms;
  }
  &:hover {
    background: #e0e0e0;
    .remove-btn {
      opacity: 1;
    }
  }
  input {
    color: #434343;
    text-decoration: none;
    font-size: 14px;
    border: 0;
    background: transparent;
    flex: 1 0 auto;
    border-bottom: 1px solid transparent;
    margin-right: 30px;
    &:focus {
      outline: none;
      border-color: #afb1b0;
    }
  }
  &.done {
    input {
      color: rgba(0, 0, 0, 0.54);
      text-decoration: line-through;
    }
  }
}

.remove-btn {
  background: url("../assets/icons/remove-icon.svg") center no-repeat;
  background-size: contain;
  border-radius: 4px;
  width: 18px;
  height: 18px;
  border: 0;
  line-height: 0;
  padding: 0;
  cursor: pointer;
  z-index: 100;
  &:hover,
  &:focus {
    background-color: #eee;
  }
  &:focus {
    outline: none;
    opacity: 1 !important;
  }
}
</style>
