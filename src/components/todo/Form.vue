<template>
  <div>
  <v-form @submit.prevent="createTask">
    <v-text-field :value="value" @input="$emit('input', $event)"
                  label="Введите название дела"
                  outlined
                  clearable
    >
    </v-text-field>
  </v-form>
</div>
</template>

<script>
export default {
  name: "Form",
  props: ['value', 'createTask'],
}
</script>

<style scoped>

</style>