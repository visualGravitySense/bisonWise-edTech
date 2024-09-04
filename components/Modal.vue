<template>
    <div v-if="isOpen" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center">
      <div class="bg-white rounded-lg p-6 max-w-lg w-full">
        <h2 class="text-xl font-bold mb-4">{{ title }}</h2>
        <slot></slot>
        <SfButton @click="closeModal" class="mt-4">Close</SfButton>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  import { SfButton } from '@storefront-ui/vue';
  
  const props = defineProps({
    isOpen: Boolean,
    title: String
  });
  
  const emit = defineEmits(['close']);
  
  function closeModal() {
    emit('close');
  }
  </script>
  