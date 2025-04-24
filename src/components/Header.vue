<script setup lang="ts">
import { useUserStore } from '../stores/user';
import { useRouter } from 'vue-router';
import robotImage from '../assets/robot.png';
import dotenv from 'dotenv';
   
dotenv.config();
const apiUrl = process.env.VUE_APP_API_URI || 'http://localhost:3000';
// const apiUrl = import.meta.env.VITE_API_URL;
const userStore = useUserStore();
const router = useRouter();

const logout = () => {
  userStore.logout();
  router.push('/');
};
</script>

<template>
  <div
    class="h-15 py-4 px-6 bg-gray-800 shadow-md flex justify-between items-center"
  >
    <img :src="robotImage" alt="Chat AI" class="w-8 h-8" />  
    <h1 class="text-lg font-semibold">Chat AI</h1>
    <button @click="logout" class="text-gray-400 hover:text-white">
      Logout
    </button>
  </div>
  <div
    class="h-0 py-4 px-6 bg-red-800 shadow-md flex justify-between items-center"
  >
  Api Url: {{apiUrl}} 
</div>
</template>
