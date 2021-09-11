<template>
    <v-radio-group
        row
        :value="value"
        @change="$emit('input', $event)"
    >
      <v-radio
          label="All"
      ></v-radio>
      <v-radio
          label="Only completed"
      ></v-radio>
      <v-radio
          label="Only in process"
      ></v-radio>
    </v-radio-group>
</template>

<script>
export default {
  name: "TaskFilter",
  props: ['value'],
}
</script>

<style scoped>

</style>