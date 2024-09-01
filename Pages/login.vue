<!-- pages/login.vue -->
<template>
    <div class="container mx-auto p-4 max-w-md">
      <h1 class="text-2xl font-bold mb-6">Login</h1>
      
      <form @submit.prevent="login">
        <!-- Ввод email -->
        <div class="mb-4">
          <label class="block text-gray-700">Email</label>
          <SfInput v-model="email" type="email" placeholder="Enter your email" class="w-full" />
        </div>
        
        <!-- Ввод пароля -->
        <div class="mb-4">
          <label class="block text-gray-700">Password</label>
          <SfInput v-model="password" type="password" placeholder="Enter your password" class="w-full" />
        </div>
  
        <!-- Кнопка входа -->
        <SfButton type="submit" class="bg-blue-600 text-white px-4 py-2 mt-4">
          Login
        </SfButton>
      </form>
  
      <!-- Ссылка на регистрацию -->
      <p class="mt-4">
        Don't have an account? <nuxt-link to="/register" class="text-blue-600">Register here</nuxt-link>.
      </p>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  import { SfButton, SfInput } from '@storefront-ui/vue';
  
  const email = ref('');
  const password = ref('');
  
  function login() {
    // Логика авторизации
    alert(`Logging in with Email: ${email.value}`);
  }
  </script>
  
  <style scoped>
  /* Дополнительные стили */
  </style>
  