<template>
  <v-container>
    <v-form @submit.prevent="createTask">
      <v-text-field
          v-model="task"
          label="Введите название дела"
          outlined
          clearable
      >
      </v-text-field>
    </v-form>
    <v-card class="mb-5" v-for="task in tasks" :key="task.id" ref="task">
      <v-list-item>
        <v-list-item-content>
          <v-checkbox
              hide-details
              class="shrink mr-2 mt-0"
          >
            <template v-slot:label>
              <div>{{ task.title }}</div>
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
export default {
  name: "ToDo",
  data() {
    return {
      task: "",
      test: true,
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
      this.tasks.unshift(newTask)
      localStorage.name = this.task;
      this.task = "";
    },
    removeTask(id) {
      let item = this.tasks.findIndex(task => task.id === id);
      this.tasks.splice(item, 1);
    }
  },
}
</script>

<style scoped>

</style>
