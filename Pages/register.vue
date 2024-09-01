<!-- pages/register.vue -->
<template>
    <div class="container mx-auto p-4 max-w-md">
      <h1 class="text-2xl font-bold mb-6">Register</h1>
      
      <form @submit.prevent="register">
        <!-- Ввод имени -->
        <div class="mb-4">
          <label class="block text-gray-700">Full Name</label>
          <SfInput v-model="fullName" placeholder="Enter your full name" class="w-full" />
        </div>
        
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
  
        <!-- Кнопка регистрации -->
        <SfButton type="submit" class="bg-green-600 text-white px-4 py-2 mt-4">
          Register
        </SfButton>
      </form>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  import { SfButton, SfInput } from '@storefront-ui/vue';
  
  const fullName = ref('');
  const email = ref('');
  const password = ref('');
  
  function register() {
    // Логика регистрации
    alert(`Registering user: ${fullName.value}`);
  }
  </script>
  
  <style scoped>
  /* Дополнительные стили */
  </style>
  