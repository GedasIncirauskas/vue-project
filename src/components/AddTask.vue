<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <input
        type="text"
        v-model="description"
        name="text"
        placeholder="Add Task"
      />
    </div>
    <div class="form-control">
      <input
        type="text"
        v-model="date"
        name="day"
        placeholder="Ex. 2021-00-00"
      />
    </div>
    <div class="form-control form-control-check">
      <label for="reminder">Add reminder?</label>
      <input type="checkbox" v-model="reminder" name="reminder" />
    </div>

    <input type="submit" value="Add to list" class="btn" />
  </form>
</template>

<script>
export default {
  name: "AddTask",
  data() {
    return {
      description: "",
      date: "",
      reminder: false,
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      if (!this.description) {
        alert("Please add a task");
        return;
      }
      const addedTask = {
        id: Math.floor(Math.random() * 10000),
        description: this.description,
        date: this.date,
        reminder: this.reminder,
      };
      this.$emit("add-task", addedTask);
      this.description = "";
      this.date = "";
      this.reminder = false;
    },
  },
};
</script>

<style scoped>
.add-form {
  margin-bottom: 1rem;
}

.form-control input {
  width: 100%;
  padding: 0.5rem;
  margin: 0.5rem auto;
  object-fit: cover;
}

.form-control label {
  width: 20rem;
  color: rgb(145, 145, 145);
}

.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 10rem;
}

.btn {
  text-align: center;
  background: rgb(0, 0, 0);
  color: rgb(232, 232, 232);
  border: none;
  padding: 0.5rem 1rem;
  margin: 0.5rem auto;
  border-radius: 0.5rem;
  cursor: pointer;
  text-decoration: none;
  font-size: 1rem;
  width: 100%;
}
</style>
