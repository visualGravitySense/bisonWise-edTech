<!-- pages/instructor/courses.vue -->
<template>
    <div class="container mx-auto p-4">
      <h1 class="text-2xl font-bold mb-6">Manage Your Courses</h1>
      
      <SfButton class="bg-green-600 text-white px-4 py-2 mb-4" @click="createCourse">
        Create New Course
      </SfButton>
      
      <!-- Список курсов инструктора -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        <CourseCard
          v-for="course in instructorCourses"
          :key="course.id"
          :course="course"
        />
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  import { SfButton } from '@storefront-ui/vue';
  import CourseCard from '~/components/CourseCard.vue';
  
  // Пример данных курсов инструктора
  const instructorCourses = ref([
    { id: 1, title: 'Vue 3 and Nuxt 3 Complete Course', instructor: 'John Doe', price: 29.99, image: 'https://via.placeholder.com/150' },
    { id: 2, title: 'Advanced JavaScript Techniques', instructor: 'John Doe', price: 49.99, image: 'https://via.placeholder.com/150' },
  ]);
  
  function createCourse() {
    alert('Course creation functionality coming soon!');
  }
  </script>
  
  <style scoped>
  /* Дополнительные стили */
  </style>
  