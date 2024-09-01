<!-- components/Header.vue -->
<template>
    <header class="bg-white shadow-md p-4 flex justify-between items-center">
      <!-- Logo -->
      <div class="text-2xl font-bold text-blue-600">
        BisonWise
      </div>
      
      <!-- Navigation -->
      <nav class="hidden md:flex space-x-6">
        <a href="/" class="text-gray-600 hover:text-blue-600">Home</a>
        <a href="/courses" class="text-gray-600 hover:text-blue-600">Courses</a>
        <a href="/about" class="text-gray-600 hover:text-blue-600">About</a>
      </nav>
      
      <!-- Login button -->
      <SfButton class="bg-blue-600 text-white px-4 py-2 rounded">
        Sign In
      </SfButton>
    </header>
  </template>
  
  <script setup>
  // import button Storefront UI
  import { SfButton } from '@storefront-ui/vue';
  </script>
  
  <style scoped>
  /* add styles*/
  </style>
   