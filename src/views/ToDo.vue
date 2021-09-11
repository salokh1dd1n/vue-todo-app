<template>
  <v-container>
    <TaskForm v-model="task" :create-task="createTask" />
    <TaskFilter v-model="filter" />
    <TaskList :tasks="filteredTasks" :remove-task="removeTask" />
  </v-container>
</template>

<script>
import TaskForm from "../components/todo/TaskForm";
import TaskFilter from "../components/todo/TaskFilter";
import TaskList from "../components/todo/TaskList";

const STORAGE_KEY = "todo-storage";
export default {
  name: "ToDo",
  components: {
    TaskForm,
    TaskFilter,
    TaskList
  },
  data() {
    return {
      task: "",
      filter: 0,
      tasks: []
    }
  },
  computed: {
    filteredTasks() {
      if(this.filter === 1) return this.tasks.filter(task => (task.completed === true));
      if(this.filter === 2) return this.tasks.filter(task => (task.completed === false))
      return this.tasks
    }
  },
  methods: {
    createTask() {
      let newTask = {
        id: this.tasks.length + 1,
        title: this.task,
        completed: false
      }
      this.tasks.unshift(newTask)
      this.task = "";
      localStorage.setItem(STORAGE_KEY, JSON.stringify(this.tasks))
    },
    removeTask(id) {
      let item = this.tasks.findIndex(task => task.id === id);
      this.tasks.splice(item, 1);
      localStorage.setItem(STORAGE_KEY, JSON.stringify(this.tasks))
    },
  },
  created() {
    this.tasks = JSON.parse(localStorage.getItem(STORAGE_KEY));
  },
  updated() {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(this.tasks))
  }
}
</script>

<style scoped>

</style>
