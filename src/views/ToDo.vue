<template>
  <v-container>
    <v-form>
      <v-text-field
          v-model="task"
          label="Введите название дела"
          outlined
          clearable
      >
      </v-text-field>
    </v-form>
    <v-card class="mb-5" v-for="task in tasks" :key="task.id">
      <v-list-item>
        <v-list-item-content>
          <v-checkbox
              hide-details
              class="shrink mr-2 mt-0"
          >
            <template v-slot:label>
              <div>Task</div>
            </template>
          </v-checkbox>
        </v-list-item-content>
        <v-list-item-action>
          <v-btn
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
          title: "Salohiddin Berdiyorov Bahriddin o'g'li ekanligimdan fahirlanaman",
          completed: false,
        },
        {
          id: 2,
          title: "First Task",
          completed: true,
        },
        {
          id: 3,
          title: "First Task",
          completed: false,
        }
      ]
    }
  },
}
</script>

<style scoped>

</style>
