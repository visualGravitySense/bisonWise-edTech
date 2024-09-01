<!-- pages/instructor/edit-course.vue -->
<template>
    <div class="container mx-auto p-4">
      <h1 class="text-2xl font-bold mb-6">{{ isEditing ? 'Edit Course' : 'Create New Course' }}</h1>
      
      <form @submit.prevent="saveCourse">
        <!-- Название курса -->
        <div class="mb-4">
          <label class="block text-gray-700">Course Title</label>
          <SfInput v-model="course.title" placeholder="Enter course title" class="w-full" />
        </div>
  
        <!-- Описание курса -->
        <div class="mb-4">
          <label class="block text-gray-700">Course Description</label>
          <SfTextarea v-model="course.description" placeholder="Enter course description" class="w-full" />
        </div>
  
        <!-- Цена курса -->
        <div class="mb-4">
          <label class="block text-gray-700">Price</label>
          <SfInput v-model="course.price" type="number" placeholder="Enter course price" class="w-full" />
        </div>
  
        <!-- Загрузка видео -->
        <div class="mb-4">
          <label class="block text-gray-700">Upload Course Video</label>
          <FileUpload v-model="course.video" accept="video/*" />
        </div>
  
        <!-- Кнопка сохранения -->
        <SfButton type="submit" class="bg-blue-600 text-white px-4 py-2">
          {{ isEditing ? 'Save Changes' : 'Create Course' }}
        </SfButton>
      </form>
    </div>
  </template>
  
  <script setup>
  import { ref, computed } from 'vue';
  import { SfButton, SfInput, SfTextarea } from '@storefront-ui/vue';
  import FileUpload from '~/components/FileUpload.vue';
  
  // Определяем редактирование или создание нового курса
  const isEditing = computed(() => !!courseId);
  const courseId = ref(null); // Замените реальным идентификатором, если редактирование
  
  const course = ref({
    title: '',
    description: '',
    price: 0,
    video: null,
  });
  
  function saveCourse() {
    // Логика сохранения курса
    alert(`Course ${isEditing.value ? 'updated' : 'created'}: ${course.value.title}`);
  }
  </script>
  
  <style scoped>
  /* Дополнительные стили */
  </style>
  