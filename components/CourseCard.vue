<!-- components/CourseCard.vue -->
<template>
    <div class="max-w-sm rounded overflow-hidden shadow-lg m-4">
      <!-- Immage -->
      <img class="w-full" :src="course.image" :alt="course.title" />
      
      <div class="px-6 py-4">
        <!-- Name -->
        <div class="font-bold text-xl mb-2">{{ course.title }}</div>
        
        <!-- Teacher -->
        <p class="text-gray-700 text-base">
          {{ course.instructor }}
        </p>
      </div>
      
      <!-- Price -->
      <div class="px-6 pt-4 pb-2 flex justify-between items-center">
        <span class="font-bold text-lg">{{ course.price }} $</span>
        <SfButton class="bg-green-600 text-white px-4 py-2 rounded">
          Add to Cart
        </SfButton>
      </div>
    </div>
  </template>
  
  <script setup>
  // 
  import { SfButton } from '@storefront-ui/vue';
  
  // props
  defineProps({
    course: {
      type: Object,
      required: true,
    },
  });
  </script>
  
  <style scoped>
  /*  */
  </style>
  