<template>
  <div
    @dblclick="onToggle(task.id)"
    :class="[task.reminder ? 'reminder' : '', 'task']"
  >
    <h3>
      {{ task.description }}
      <i @click="onDelete(task.id)" class="fas fa-times"></i>
    </h3>
    <p>{{ task.date }}</p>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
  methods: {
    onDelete(id) {
      this.$emit("delete-task", id);
    },
    onToggle(id) {
      this.$emit("toggle-reminder", id);
    },
  },
};
</script>

<style scope>
.fas {
  color: rgb(233, 0, 0);
  line-height: 0.5rem;
}
.task {
  background: #e6e6e6;
  margin: 0.5rem;
  padding: 0.5rem 1.5rem;
  cursor: pointer;
}
.task.reminder {
  border-left: 0.5rem solid rgb(1, 221, 1);
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
