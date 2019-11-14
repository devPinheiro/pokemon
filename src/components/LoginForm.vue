<template>
  <div class="w-full">
    <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4" @submit.prevent="submit">
      <div class="mb-4">
        <label class="block text-gray-700 text-sm font-bold mb-2" for="email">Username</label>
        <input
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
          :class="{'border-red-500': $v.username.$error}"
          id="username"
          type="text"
          placeholder="John"
          v-model.trim="$v.username.$model"
        />

        <p
          class="text-red-500 text-xs italic"
          v-if="!$v.username.required"
        >Please provide your username</p>
      </div>
      <div class="mb-6">
        <label class="block text-gray-700 text-sm font-bold mb-2" for="password">Password</label>
        <input
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline"
          :class="{'border-red-500': $v.password.$error}"
          id="password"
          type="password"
          placeholder
          v-model.trim="$v.password.$model"
        />
        <p
          class="text-red-500 text-xs italic"
          v-if="!$v.password.required"
        >Please provide your password.</p>
        <p
          class="text-red-500 text-xs italic"
          v-if="!$v.password.minLength"
        >Password must be at least 
        {{ $v.password.$params.minLength.min }} 
        characters</p>
      </div>
      <div class="flex items-center justify-between">
        <button
          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
          :class="{'opacity-50 cursor-not-allowed': $v.$error}"
          type="submit"
          :disabled="$v.$error"
        >
        Sign In
        </button>
      </div>
    </form>
  </div>
</template>

<script>
// import vuelidate library for basic form validation
import { required, minLength } from "vuelidate/lib/validators/";

export default {
  data() {
    return {
      username: "",
      password: ""
    };
  },
  // add validation rules for email and password fields
  validations: {
    username: {
      required
    },
    password: {
      required,
      minLength: minLength(6)
    }
  },
  methods: {
    // handles form submission
    submit() {
      this.$v.$touch();
      if (!this.$v.$invalid) {
        // persist user credential to localstorage
        localStorage.setItem('pokermonUser', JSON.stringify({
          username: this.username,
          password: this.password
        }));
        // redirect to the next page
        this.$router.push('/dashboard')
      }
    }
  }
};
</script>

<style scoped></style>
