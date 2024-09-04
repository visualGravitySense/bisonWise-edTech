<template>
  <div class="course-card bg-white shadow-lg rounded-lg p-4">
    <img :src="course.image" alt="Course image" class="rounded-t-lg w-full h-48 object-cover">
    <div class="p-4">
      <h2 class="text-xl font-bold">{{ course.title }}</h2>
      <p class="text-gray-600">{{ course.description }}</p>
      <p class="text-blue-500 font-semibold mt-2">{{ course.price }}</p>
      <SfButton @click="goToCourse(course.id)" class="mt-4">View Course</SfButton>
    </div>
  </div>
</template>

<script setup>
import { SfButton } from '@storefront-ui/vue';
import { useRouter } from 'vue-router';

const props = defineProps({
  course: {
    type: Object,
    required: true
  }
});

const router = useRouter();

function goToCourse(id) {
  router.push(`/courses/${id}`);
}
</script>

<style scoped>
.course-card {
  max-width: 320px;
}
</style>
