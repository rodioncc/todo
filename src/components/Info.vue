<template>
  <div class="info">
    <p>Completed Tasks: {{ completedTasks.length }}</p>
    <p>Pending Tasks: {{ pendingTasks.length }}</p>
  </div>
</template>

<script>
export default {
  name: "Info",
  props: ["completedTasks", "pendingTasks"]
};
</script>

<style scoped lang="scss">
.info {
  color: #b0b0b0;
  font-size: 12px;
  border-top: 1px solid rgba(0, 0, 0, 0.1);
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  padding: 8px 10px;
  background: #fff;
  p {
    margin: 0;
    &:first-child {
      margin-bottom: 5px;
    }
  }
}
</style>
