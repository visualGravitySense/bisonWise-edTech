<template>
  <div class="courses-page">
    <Header />
    <div class="container mx-auto p-6">
      <h1 class="text-2xl font-bold mb-4">All Courses</h1>
      <CourseFilter />
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
        <CourseCard v-for="course in courses" :key="course.id" :course="course" />
      </div>
    </div>
    <Footer />
  </div>
</template>

<script setup>
import Header from '~/components/Header.vue';
import Footer from '~/components/Footer.vue';
import CourseCard from '~/components/CourseCard.vue';
import CourseFilter from '~/components/CourseFilter.vue';

// Пример данных курсов, которые можно заменить на реальный API вызов
const courses = [
  { id: 1, title: 'Vue.js Basics', description: 'Learn the basics of Vue.js', price: '$49', image: 'path/to/image' },
  { id: 2, title: 'Advanced Vue.js', description: 'Take your Vue.js skills to the next level', price: '$99', image: 'path/to/image' },
  // Добавьте больше курсов
];
</script>
