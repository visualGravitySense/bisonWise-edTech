<template>
    <div class="user-management">
      <h2 class="text-2xl font-bold mb-4">User Management</h2>
      <table class="table-auto w-full">
        <thead>
          <tr>
            <th class="px-4 py-2">Name</th>
            <th class="px-4 py-2">Email</th>
            <th class="px-4 py-2">Role</th>
            <th class="px-4 py-2">Actions</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="user in users" :key="user.id">
            <td class="border px-4 py-2">{{ user.name }}</td>
            <td class="border px-4 py-2">{{ user.email }}</td>
            <td class="border px-4 py-2">{{ user.role }}</td>
            <td class="border px-4 py-2">
              <SfButton @click="editUser(user.id)">Edit</SfButton>
              <SfButton @click="blockUser(user.id)" class="ml-2">Block</SfButton>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script setup>
  import { SfButton } from '@storefront-ui/vue';
  
  const props = defineProps({
    users: Array
  });
  
  function editUser(id) {
    console.log('Edit user with ID:', id);
  }
  
  function blockUser(id) {
    console.log('Block user with ID:', id);
  }
  </script>
  