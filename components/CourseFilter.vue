<template>
    <div class="flex space-x-4 mb-4">
      <SfInput v-model="search" placeholder="Search Courses" />
      <SfSelect v-model="category" :options="categories" placeholder="Category" />
      <SfSelect v-model="sort" :options="sortOptions" placeholder="Sort By" />
      <SfButton @click="applyFilters">Apply</SfButton>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  import { SfInput, SfSelect, SfButton } from '@storefront-ui/vue';
  
  const search = ref('');
  const category = ref('');
  const sort = ref('');
  
  const categories = ['Development', 'Design', 'Marketing'];
  const sortOptions = ['Popularity', 'Rating', 'Price'];
  
  function applyFilters() {
    console.log('Filters applied:', { search: search.value, category: category.value, sort: sort.value });
  }
  </script>
  