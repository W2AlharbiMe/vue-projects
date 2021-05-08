<template>
  <div class="container">
    <Header @onTask:toggleForm="handleToggleForm" :showAddTaskForm="showAddTaskForm" title="Task Tracker" />
    <AddTask v-if="showAddTaskForm" @onTask:add="handleAddTask" />
    <Tasks
      @onTask:delete="handleTaskDelete"
      @onTask:toggle="handleReminderToggle"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import Header from "./components/Header";
import Tasks from "./components/Tasks";
import AddTask from "./components/AddTask";

export default {
  name: "App",
  components: { Header, Tasks, AddTask },
  data: () => ({
    tasks: [],
    showAddTaskForm: false,
  }),
  created() {
    this.tasks = [
      this.__createTask(1, "Doctors Appointment", "March 1st at 2:30pm", true),
      this.__createTask(2, "Meeting at work", "March 3rd at 1:30pm", true),
      this.__createTask(3, "Food Shopping", "March 3rd at 11:00am", false),
    ];
  },
  methods: {
    __createTask: (id, text, day, reminder) => ({ id, text, day, reminder }),
    handleTaskDelete(id) {
      this.tasks = this.tasks.filter((t) => t.id !== id);
    },
    handleReminderToggle(id) {
      this.tasks = this.tasks.map((t) =>
        t.id === id ? { ...t, reminder: !t.reminder } : t
      );
    },
    handleAddTask(task) {
      task.id = this.tasks.length + 1;
      this.tasks = [...this.tasks, task];
    },
    handleToggleForm() {
      this.showAddTaskForm = !this.showAddTaskForm;
    }
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Poppins", sans-serif;
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
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
  transition: 250ms ease-out;
}
.btn:hover {
  background: #0077ff;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
