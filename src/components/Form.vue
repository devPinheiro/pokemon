<template>
 <div class="w-full max-w-xs  m-auto">
  <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4" @submit.prevent="submit">
    <div class="mb-4">
      <label class="block text-gray-700 text-sm font-bold mb-2" for="email">
        Email
      </label>
      <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" :class="{'border-red-500': $v.email.$error}" id="username" type="email" placeholder="example@mail.com"
      v-model.trim="$v.email.$model">
      <p class="text-red-500 text-xs italic" v-if="!$v.email.email">Please provide a valid email</p>  
      <p class="text-red-500 text-xs italic" v-if="!$v.email.required">Please provide an email</p> 
    </div>
    <div class="mb-6">
      <label class="block text-gray-700 text-sm font-bold mb-2" for="password">
        Password
      </label>
      <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline" :class="{'border-red-500': $v.password.$error}" id="password" type="password" placeholder=""  v-model.trim="$v.password.$model">
      <p class="text-red-500 text-xs italic" v-if="!$v.password.required">Please provide your password.</p>
       <p class="text-red-500 text-xs italic" v-if="!$v.password.minLength">Password must be at least {{ $v.password.$params.minLength.min }} characters</p>
    </div>
    <div class="flex items-center justify-between">
      <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" :class="{'opacity-50 cursor-not-allowed': $v.$error}" type="submit" :disabled="$v.$error">
        Sign In
      </button>  
    </div>
  </form> 
</div>

</template>

<script>
   // import vuelidate library for basic form validation
  import { required, minLength, email } from 'vuelidate/lib/validators/';

  export default {
    data() {
      return {
        email: '',
        password: ''
      }
    }, 
    // add validation rules for email and password fields
    validations: {
      email: {
        required,
        email
        },
      password: {
        required,
        minLength: minLength(6)
        }
    },
    methods: {
      // handles form submission
      submit () {
        this.$v.$touch()
        if(this.$v.$invalid){
         alert('error')
        } else{
          alert('submitted')
         
        }
         
      }
    }
  }
</script>

<style scoped>

</style>