<!-- pages/index.vue -->
<template>
  <div>
    <!-- Header -->
    <Header />

    <!-- Main Content -->
    <main class="container mx-auto p-6">
      <h1 class="text-3xl font-bold mb-6">Featured Courses</h1>
      
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        <CourseCard
          v-for="course in courses"
          :key="course.id"
          :course="course"
        />
      </div>
    </main>

    <!-- Footer -->
    <Footer />
  </div>
</template>

<script setup>
// Components import
import Header from '~/components/Header.vue';
import Footer from '~/components/Footer.vue';
import CourseCard from '~/components/CourseCard.vue';

// Template classes
const courses = [
  {
    id: 1,
    image: 'https://via.placeholder.com/150',
    title: 'Vue 3 and Nuxt 3 Complete Course',
    instructor: 'John Doe',
    price: 29.99,
  },
  {
    id: 2,
    image: 'https://via.placeholder.com/150',
    title: 'Tailwind CSS Mastery',
    instructor: 'Jane Smith',
    price: 19.99,
  },
  // 
];
</script>

<style scoped>
/*  */
</style>
