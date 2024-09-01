<!-- pages/courses/[id].vue -->
<template>
    <div class="container mx-auto p-4">
      <div class="flex flex-col md:flex-row">
        <!-- Course immage -->
        <img :src="course.image" :alt="course.title" class="w-full md:w-1/3 rounded-lg shadow-md mb-4 md:mb-0" />
        
        <!-- Course description -->
        <div class="md:ml-6">
          <h1 class="text-3xl font-bold mb-2">{{ course.title }}</h1>
          <p class="text-gray-700 mb-4">Instructor: {{ course.instructor }}</p>
          <p class="text-lg font-bold mb-4">{{ course.price }} $</p>
          <p class="text-gray-600 mb-4">{{ course.description }}</p>
          
          <!-- Add course -->
          <SfButton class="bg-green-600 text-white px-4 py-2" @click="addToCart">
            Add to Cart
          </SfButton>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { SfButton } from '@storefront-ui/vue';
  import { useCartStore } from '~/stores/cart';
  
  // Course ID from route
  const route = useRoute();
  const courseId = route.params.id;
  
  // Courses
  const courses = [
    { id: 1, title: 'Vue 3 and Nuxt 3 Complete Course', instructor: 'John Doe', price: 29.99, image: 'https://via.placeholder.com/150', description: 'Learn Vue 3 and Nuxt 3 from scratch.' },
    { id: 2, title: 'Tailwind CSS Mastery', instructor: 'Jane Smith', price: 19.99, image: 'https://via.placeholder.com/150', description: 'Master Tailwind CSS in this comprehensive course.' },
    { id: 3, title: 'JavaScript for Beginners', instructor: 'Alex Johnson', price: 39.99, image: 'https://via.placeholder.com/150', description: 'An introductory course to JavaScript.' },
    // 
  ];
  
  // Course searching by ID
  const course = courses.find(c => c.id == courseId);
  
  // Adding course to buy
  const cartStore = useCartStore();
  function addToCart() {
    cartStore.addToCart(course);
    alert('Course added to cart!');
  }
  </script>
  
  <style scoped>
  /*  */
  </style>
  