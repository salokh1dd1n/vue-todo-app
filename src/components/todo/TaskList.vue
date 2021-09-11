<template>
  <div id="task-list">
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
  </div>
</template>

<script>
export default {
  name: "TaskList",
  props: {
    tasks: Array,
    removeTask: Function,
  },
}
</script>

<style scoped>

</style>