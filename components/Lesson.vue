<template>
    <div class="lesson">
      <video controls :src="lesson.videoUrl" class="w-full mb-4"></video>
      <h2 class="text-2xl font-bold mb-2">{{ lesson.title }}</h2>
      <p class="text-gray-700 mb-4">{{ lesson.description }}</p>
      <div class="flex justify-between">
        <SfButton v-if="previousLesson" @click="goToLesson(previousLesson.id)">Previous</SfButton>
        <SfButton v-if="nextLesson" @click="goToLesson(nextLesson.id)">Next</SfButton>
      </div>
    </div>
  </template>
  
  <script setup>
  import { SfButton } from '@storefront-ui/vue';
  import { useRouter } from 'vue-router';
  
  const props = defineProps({
    lesson: Object,
    previousLesson: Object,
    nextLesson: Object
  });
  
  const router = useRouter();
  
  function goToLesson(id) {
    router.push(`/lessons/${id}`);
  }
  </script>
  