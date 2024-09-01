<!-- components/CategoryCard.vue -->
<template>
    <div class="category-card border rounded-lg shadow-sm hover:shadow-md transition-shadow duration-200 cursor-pointer p-4">
      <div class="category-image mb-3">
        <img :src="category.image" :alt="category.name" class="w-full h-40 object-cover rounded-lg" />
      </div>
      <div class="category-name text-center">
        <h3 class="text-lg font-semibold text-gray-800">{{ category.name }}</h3>
      </div>
    </div>
  </template>
  
  <script setup>
  defineProps({
    category: {
      type: Object,
      required: true
    }
  });
  </script>
  
  <style scoped>
  .category-card {
    max-width: 200px;
  }
  
  .category-image img {
    transition: transform 0.3s;
  }
  
  .category-card:hover .category-image img {
    transform: scale(1.05);
  }
  </style>
  