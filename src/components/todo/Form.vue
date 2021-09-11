<template>
  <v-form @submit.prevent="submit">
    <v-text-field :value="value"
                  @input="$emit('input', $event)"
                  :error-messages="taskError"
                  label="Введите название дела"
                  outlined
                  clearable
                  autocomplete="off"
                  hide-details="auto"
    >
    </v-text-field>
  </v-form>
</template>

<script>
import {validationMixin} from "vuelidate"
import {required, minLength} from "vuelidate/lib/validators"

export default {
  name: "Form",
  props: ['value', 'createTask'],
  mixins: [validationMixin],
  computed: {
    taskError() {
      const errors = []
      if (!this.$v.value.$dirty) return errors
      !this.$v.value.minLength && errors.push('Task must be at least 5 characters long')
      !this.$v.value.required && errors.push('Task is required.')
      return errors
    },
  },
  methods: {
    submit() {
      this.$v.$touch();
      if (!this.$v.$invalid)
        this.createTask();
    }
  },
  validations: {
    value: {
      required,
      minLength: minLength(5),
    }
  }
}
</script>

<style scoped>

</style>