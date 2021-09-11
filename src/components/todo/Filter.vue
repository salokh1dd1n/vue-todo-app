<template>
  <v-radio-group
      row
      class="float-end"
      v-model="filter"
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
  name: "Filter",
  data() {
    return {
      filter: "",
    }
  }
}
</script>

<style scoped>

</style>