<template>
  <header>
    <h1>{{ title }}</h1>
    <Button
      :name="showTasks ? 'Close' : 'Add Task'"
      @toggle-add="$emit('toggle-add')"
    />
  </header>
</template>

<script>
import Button from "./Button.vue";
export default {
  name: "Header",
  props: {
    title: {
      type: String,
    },
    showTasks: Boolean,
  },
  components: {
    Button,
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 2rem;
}
</style>
