<script setup lang="ts">
import { ref } from 'vue'
import axios from "axios"

const name = ref('')
const email = ref('')
const password = ref('')
type RegisterResponse = void

const register = async() => {
  console.log(name.value, email.value, password.value)

  try {   
    const res = await axios.post<RegisterResponse>('http://localhost:8080/register', {
      name: name.value,
      email: email.value,
      password: password.value
    })    
    alert('User registered successfully')    

  } catch (error) {
    alert('Error registering user')    
  }
}

</script>

<template>
  <div class=" bg-blue-100 ">
    <form class="flex flex-col items-center justify-center h-screen" v-on:submit.prevent="register">

      <h1 class="h-25 text-4xl font-bold">Register</h1>
      
      <div class="flex flex-col items-center justify-center gap-8">            
        <input type="text" v-model="name" placeholder="Name" class="border-2 p-2 w-100">
        <input type="text" v-model="email" placeholder="Email" class="border-2 p-2 w-100">
        <input type="password" v-model="password" placeholder="Password" class="border-2 p-2 w-100">
      </div>    
      
        <button type="submit" class="border rounded-xl w-30 m-5 cursor-pointer">Registrar</button>
              
    </form>
  </div>
</template>


