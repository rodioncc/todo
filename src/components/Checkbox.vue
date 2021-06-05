<template>
  <button
    @click.prevent="onCheck"
    :class="['checkbox', { check: todo.done }]"
  />
</template>

<script>
export default {
  name: "Checkbox",
  props: ["todo"],
  methods: {
    onCheck() {
      this.$emit("on-check", this.todo);
    }
  }
};
</script>

<style scoped lang="scss">
.checkbox {
  border: 0;
  background: url("../assets/icons/no-check.svg") center no-repeat;
  background-size: contain;
  width: 18px;
  height: 18px;
  padding: 0;
  cursor: pointer;
  line-height: 0;
  svg {
    fill: #777;
    height: 18px;
  }
  &:focus {
    outline: none;
  }
  &.check {
    background: url("../assets/icons/check.svg") center no-repeat;
  }
}
</style>
