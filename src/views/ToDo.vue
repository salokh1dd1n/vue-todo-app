<template>
  <v-container>
    <Form v-model="task" :create-task="createTask"></Form>
    <v-card class="mb-5" v-for="task in tasks" :key="task.id" ref="task">
      <v-list-item>
        <v-list-item-content>
          <v-checkbox
              v-model="task.completed"
              hide-details
              class="shrink mr-2 mt-0"
          >
            <template v-slot:label>
              <div :class="{'text-decoration-line-through': task.completed === true}">{{ task.title }}</div>
            </template>
          </v-checkbox>
        </v-list-item-content>
        <v-list-item-action>
          <v-btn @click="removeTask(task.id)"
                 color="error"
                 ripple
          >
            <v-icon color="white" left>
              mdi-trash-can
            </v-icon>
            Delete
          </v-btn>
        </v-list-item-action>
      </v-list-item>
    </v-card>
  </v-container>
</template>

<script>
import Form from "../components/todo/Form";

const STORAGE_KEY = "todo-storage";
export default {
  name: "ToDo",
  components: {Form},
  data() {
    return {
      task: "",
      test: '',
      tasks: [
        {
          id: 1,
          title: "Task #1",
          completed: false,
        },
        {
          id: 2,
          title: "Task #2",
          completed: true,
        },
        {
          id: 3,
          title: "Task #3",
          completed: false,
        }
      ]
    }
  },
  methods: {
    createTask() {
      let newTask = {
        id: this.tasks.length + 1,
        title: this.task,
        completed: false
      }
      console.log(this.task);
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
