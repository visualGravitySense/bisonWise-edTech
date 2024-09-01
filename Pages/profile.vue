<!-- pages/profile.vue -->
<template>
    <div class="container mx-auto p-4">
      <h1 class="text-2xl font-bold mb-6">Profile</h1>
      
      <!-- Info about user -->
      <section class="mb-8">
        <h2 class="text-xl font-semibold mb-2">Personal Information</h2>
        <p><strong>Name:</strong> {{ user.name }}</p>
        <p><strong>Email:</strong> {{ user.email }}</p>
        <SfButton class="bg-blue-600 text-white px-4 py-2 mt-4" @click="editProfile">
          Edit Profile
        </SfButton>
      </section>
  
      <!-- Courses -->
      <section>
        <h2 class="text-xl font-semibold mb-4">My Courses</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          <CourseCard
            v-for="course in myCourses"
            :key="course.id"
            :course="course"
          />
        </div>
      </section>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  import { SfButton } from '@storefront-ui/vue';
  import CourseCard from '~/components/CourseCard.vue';
  
  // User data example
  const user = ref({
    name: 'John Doe',
    email: 'john.doe@example.com',
  });
  
  // User courses example
  const myCourses = ref([
    { id: 1, title: 'Vue 3 and Nuxt 3 Complete Course', instructor: 'John Doe', price: 29.99, image: 'https://via.placeholder.com/150' },
    { id: 2, title: 'Tailwind CSS Mastery', instructor: 'Jane Smith', price: 19.99, image: 'https://via.placeholder.com/150' },
  ]);
  
  function editProfile() {
    alert('Edit Profile functionality coming soon!');
  }
  </script>
  
  <style scoped>
  /*  */
  </style>
  