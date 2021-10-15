<template>
  <div class="container">
    <Header
      title="Task lists"
      @toggle-add="toggleNewTask"
      :showTasks="showTasks"
    />
    <section>
      <AddTask v-show="showTasks" @add-task="addTask" />
    </section>
    <Tasks @toggle-reminder="toggle" @delete-task="deleteTask" :tasks="tasks" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";

export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
      showTasks: false,
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
    addTask(addedTask) {
      this.tasks = [...this.tasks, addedTask];
    },
    toggleNewTask() {
      this.showTasks = !this.showTasks;
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
  max-width: 30rem;
  margin: 1rem auto;
  overflow: auto;
  border: 0.1rem solid rgb(0, 24, 43);
  padding: 1.5rem;
  border-radius: 0.1rem;
}
</style>
