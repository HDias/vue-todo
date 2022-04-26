<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <p>{{ progress.toFixed(0) }} %</p>
    <ProgressBar :progress-value="progress" />
    <AddTask @task="addTask" />
    <ListTask :tasks="tasks" @remove="removeTask" @handle="handleTask" />
  </div>
</template>

<script>
import AddTask from "./components/AddTask.vue";
import ListTask from "./components/ListTask.vue";
import ProgressBar from "./components/ProgressBar.vue";

export default {
  name: "App",
  components: {
    AddTask,
    ListTask,
    ProgressBar,
  },

  data() {
    return {
      tasks: [],
    };
  },

  mounted() {
    if (localStorage.getItem("tasks")) {
      try {
        this.tasks = JSON.parse(localStorage.getItem("tasks"));
      } catch (error) {
        localStorage.removeItem("tasks");
      }
    }
  },

  computed: {
    progress() {
      const doneTasks = this.tasks.filter((task) => task.done);

      if (doneTasks.length > 0) {
        return (doneTasks.length * 100) / this.tasks.length;
      }

      return 0;
    },
  },

  methods: {
    addTask(task) {
      this.tasks.push(task);

      this.saveTasks();
    },

    removeTask(index) {
      this.tasks.splice(index, 1);

      this.saveTasks();
    },

    handleTask(index) {
      this.tasks[index].done = !this.tasks[index].done;

      this.saveTasks();
    },

    saveTasks() {
      const parsedTasks = JSON.stringify(this.tasks);

      localStorage.setItem("tasks", parsedTasks);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
