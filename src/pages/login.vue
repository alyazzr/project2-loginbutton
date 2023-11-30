<script setup lang="ts">
import { ref } from 'vue'
import { useRouter } from 'vue-router';
import { useAuthStore } from "@/stores/auth"
import axios from 'axios'

const auth = useAuthStore()
const username = ref('')
const password = ref('')
const router = useRouter()

const onLogin = async() => {
  const response = await fetch('http://localhost:3000/login/', {
    method: "post",
    headers: {
      "Content-Type": "application/json"
    },
    body: JSON.stringify({
      username: username.value,
      password: password.value
    })
  })
  

  const data = await response.json()
  console.log(data)
  
  if (data.status == "success"){

  }
  else {
    (data.status == "data yang anda masukkan tidak valid")
  }
}
</script>

<template>
    <div>
        <h1>Login Page</h1>
        <form action="" class="flex flex-col gap-2">
            <input type="text" v-model="username" class="border p-3" placeholder="Username"/>
            <input type="text" v-model="password" class="border p-3" placeholder="Password"/>
            <button type="button" class="bg-blue-500 text-white py-1 px-3" @click="onLogin">Login</button>
        </form>
    </div>

</template>
