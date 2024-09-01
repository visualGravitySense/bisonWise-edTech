<!-- pages/courses/index.vue -->
<template>
    <div class="container mx-auto p-4">
      <h1 class="text-3xl font-bold mb-6">All Courses</h1>
      
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        <CourseCard
          v-for="course in courses"
          :key="course.id"
          :course="course"
        />
      </div>
    </div>
  </template>
  
  <script setup>
  import CourseCard from '~/components/CourseCard.vue';
  
  // Courses
  const courses = [
    { id: 1, title: 'Vue 3 and Nuxt 3 Complete Course', instructor: 'John Doe', price: 29.99, image: 'https://via.placeholder.com/150' },
    { id: 2, title: 'Tailwind CSS Mastery', instructor: 'Jane Smith', price: 19.99, image: 'https://via.placeholder.com/150' },
    { id: 3, title: 'JavaScript for Beginners', instructor: 'Alex Johnson', price: 39.99, image: 'https://via.placeholder.com/150' },
    // Add more courses
  ];
  </script>
  
  <style scoped>
  /* Add styles */
  </style>
  