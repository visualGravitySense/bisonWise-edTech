<!-- pages/index.vue -->
<template>
  <div>
    <!-- Header -->
    <Header />

    

    <!-- Main Content -->
    <main class="container mx-auto p-6">

      <header class="mb-10">
        <h1 class="text-4xl font-bold mb-4">Welcome to Our EdTech Platform</h1>
        <p class="text-lg text-gray-600">Learn from the best instructors in the world.</p>
      </header>
      
      <h2 class="text-3xl font-bold mb-6">Featured Courses</h2>
      
      <CourseFilter/>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        <CourseCard
          v-for="course in courses"
          :key="course.id"
          :course="course"
        />
      </div>
    </main>

    <!-- Courses categories -->
    <section>
      <h2 class="text-2xl font-bold mb-4">Explore Categories</h2>
      <div class="flex flex-wrap gap-4">
        <CategoryCard
          v-for="category in categories"
          :key="category.id"
          :category="category"
        />
      </div>
    </section>

    <!-- Footer -->
    <Footer />
  </div>
</template>

<script setup>
// Components import
import Header from '~/components/Header.vue';
import Footer from '~/components/Footer.vue';
import CourseCard from '~/components/CourseCard.vue';
import CategoryCard from '~/components/CategoryCard.vue';
import CourseFilter from '~/components/CourseFilter.vue';

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

// Courses : categories
const categories = [
  { id: 1, name: 'Web Development', image: 'https://via.placeholder.com/150' },
  { id: 2, name: 'Data Science', image: 'https://via.placeholder.com/150' },
  { id: 3, name: 'Business', image: 'https://via.placeholder.com/150' },
  // Add more categories
];
</script>

<style scoped>
/*  */
</style>
