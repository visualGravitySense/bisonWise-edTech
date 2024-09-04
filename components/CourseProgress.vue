<template>
    <div class="bg-gray-100 p-4 rounded-lg">
      <h3 class="text-lg font-bold mb-2">Course Progress</h3>
      <SfProgress :value="progress" class="mb-2" />
      <p>{{ progress }}% complete</p>
    </div>
  </template>
  
  <script setup>
  import { SfProgress } from '@storefront-ui/vue';
  
  const props = defineProps({
    progress: {
      type: Number,
      required: true
    }
  });
  </script>
  