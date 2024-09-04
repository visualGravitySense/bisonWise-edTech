<template>
  <header class="bg-white shadow-md py-4 px-8">
    <div class="flex justify-between items-center">
      <img src="" alt="Logo" class="h-10">
      <nav class="space-x-4">
        <SfButton as="a" href="/" class="text-gray-700">Home</SfButton>
        <SfButton as="a" href="/courses" class="text-gray-700">Courses</SfButton>
        <SfButton as="a" href="/profile" class="text-gray-700">Profile</SfButton>
        <SfButton as="a" href="/login" class="text-blue-600">Login</SfButton>
      </nav>
    </div>
  </header>
</template>

<script setup>
import { SfButton } from '@storefront-ui/vue';
</script>
