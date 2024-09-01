<!-- components/FileUpload.vue -->
<template>
    <div class="file-upload mb-4">
      <label class="block text-gray-700 mb-2">{{ label }}</label>
      <div class="flex items-center">
        <input
          type="file"
          :accept="accept"
          class="hidden"
          ref="fileInput"
          @change="handleFileChange"
        />
        <SfButton type="button" class="bg-blue-600 text-white px-4 py-2" @click="triggerFileInput">
          Select File
        </SfButton>
        <span v-if="fileName" class="ml-4 text-gray-600">{{ fileName }}</span>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref, toRefs } from 'vue';
  import { SfButton } from '@storefront-ui/vue';
  
  const props = defineProps({
    modelValue: {
      type: [File, Array],
      default: null,
    },
    accept: {
      type: String,
      default: '', // Например, "video/*,image/*"
    },
    label: {
      type: String,
      default: 'Upload File',
    },
  });
  
  const emit = defineEmits(['update:modelValue']);
  
  const { modelValue } = toRefs(props);
  const fileInput = ref(null);
  const fileName = ref(modelValue.value ? (Array.isArray(modelValue.value) ? modelValue.value.map(file => file.name).join(', ') : modelValue.value.name) : '');
  
  function triggerFileInput() {
    fileInput.value.click();
  }
  
  function handleFileChange(event) {
    const files = event.target.files;
    if (files.length > 0) {
      if (files.length === 1) {
        fileName.value = files[0].name;
        emit('update:modelValue', files[0]);
      } else {
        fileName.value = Array.from(files).map(file => file.name).join(', ');
        emit('update:modelValue', Array.from(files));
      }
    } else {
      fileName.value = '';
      emit('update:modelValue', null);
    }
  }
  </script>
  
  <style scoped>
  .file-upload {
    max-width: 400px;
  }
  </style>
  