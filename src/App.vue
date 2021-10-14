<template>
  <div class="container">
    <Header title="Task lists" />
    <Tasks @toggle-reminder="toggle" @delete-task="deleteTask" :tasks="tasks" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";

export default {
  name: "App",
  components: {
    Header,
    Tasks,
  },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
    toggle(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },
  },

  created() {
    this.tasks = [
      {
        id: 1,
        description: "Do home work",
        date: "2021-10-15",
        reminder: false,
      },
      {
        id: 2,
        description: "Order pizza for Friday",
        date: "2021-10-14",
        reminder: true,
      },
      {
        id: 3,
        description: "Write to Kim",
        date: "2021-10-12",
        reminder: false,
      },
    ];
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
</style>
