<template>
  <b-form @submit.stop.prevent="onSubmit">
    <b-form-group id="example-input-group-1" label="Name" label-for="input-1">
      <b-form-input
        id="input-1"
        v-model="$v.form.username.$model"
        name="input-1"
        :state="validateState('username')"
        aria-describedby="input-1-live-feedback"
      ></b-form-input>

      <b-form-invalid-feedback id="input-1-live-feedback"
        >This is a required field and must be at least 3
        characters.</b-form-invalid-feedback
      >
    </b-form-group>

    <b-form-group id="input-group-2" label="Email" label-for="input-2">
      <b-form-input
        id="input-2"
        v-model="$v.form.email.$model"
        name="input-2"
        :state="validateState('email')"
        aria-describedby="input-2-live-feedback"
      ></b-form-input>

      <b-form-invalid-feedback id="input-2-live-feedback"
        >This is a required field and must be at least 3 and less then 20
        characters.</b-form-invalid-feedback
      >
    </b-form-group>

    <b-form-group
      id="input-group-3"
      label="Password"
      label-for="example-input-3"
    >
      <b-form-input
        id="input-3"
        v-model="$v.form.password.$model"
        name="input-1"
        :state="validateState('password')"
        aria-describedby="input-3-live-feedback"
        type="password"
      ></b-form-input>

      <b-form-invalid-feedback id="input-3-live-feedback"
        >This is a required field and must be at least 5 and less then 50
        characters.</b-form-invalid-feedback
      >
    </b-form-group>

    <b-form-group id="input-group-4" label="Password" label-for="input-4">
      <b-form-input
        id="input-4"
        v-model="$v.form.passwordRepeat.$model"
        name="input-4"
        :state="validateState('passwordRepeat')"
        aria-describedby="input-4-live-feedback"
        type="password"
      ></b-form-input>

      <b-form-invalid-feedback id="input-4-live-feedback"
        >This is a required field and must be must match the above
        password.</b-form-invalid-feedback
      >
    </b-form-group>

    <b-button type="submit" variant="primary">Submit</b-button>
    <b-button class="ml-2" @click="resetForm()">Reset</b-button>
  </b-form>
</template>

<script>
import { validationMixin } from 'vuelidate'
import {
  required,
  minLength,
  email,
  sameAs,
  maxLength,
} from 'vuelidate/lib/validators'

export default {
  mixins: [validationMixin],
  data() {
    return {
      form: {
        username: null,
        email: null,
        password: null,
        passwordRepeat: null,
      },
    }
  },
  validations: {
    form: {
      email: {
        required,
        email,
      },
      username: {
        required,
        minLength: minLength(3),
        maxLength: maxLength(20),
      },
      password: {
        required,
        minLength: minLength(5),
        maxLength: maxLength(50),
      },
      passwordRepeat: {
        required,
        samePassword: sameAs('password'),
      },
    },
  },
  methods: {
    validateState(name) {
      const { $dirty, $error } = this.$v.form[name]
      return $dirty ? !$error : null
    },
    resetForm() {
      this.form = {
        username: null,
        email: null,
        password: null,
        passwordRepeat: null,
      }
      this.$nextTick(() => {
        this.$v.$reset()
      })
    },
    onSubmit() {
      this.$v.form.$touch()
      if (this.$v.form.$anyError) {
        return
      }

      alert('Form submitted!')
    },
  },
}
</script>

<style lang="scss" scoped></style>
