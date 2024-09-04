<template>
    <div class="quiz">
      <h2 class="text-2xl font-bold mb-4">Quiz: {{ quiz.title }}</h2>
      <div v-for="(question, index) in quiz.questions" :key="index" class="mb-4">
        <p>{{ question.text }}</p>
        <div class="space-y-2">
          <SfCheckbox v-for="option in question.options" :key="option" :label="option" v-model="answers[index]" />
        </div>
      </div>
      <SfButton @click="submitQuiz" class="mt-4">Submit Quiz</SfButton>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  import { SfButton, SfCheckbox } from '@storefront-ui/vue';
  
  const props = defineProps({
    quiz: Object
  });
  
  const answers = ref([]);
  
  function submitQuiz() {
    console.log('Quiz submitted:', answers.value);
  }
  </script>
  