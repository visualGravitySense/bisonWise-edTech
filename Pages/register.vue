<template>
  <div class="register-page">
    <Header />
    <div class="container mx-auto p-6">
      <h1 class="text-2xl font-bold mb-4">Register</h1>
      <div class="bg-white p-6 rounded-lg shadow-md">
        <SfInput v-model="user.name" placeholder="Full Name" />
        <SfInput v-model="user.email" placeholder="Email Address" class="mt-4" />
        <SfInput type="password" v-model="user.password" placeholder="Password" class="mt-4" />
        <SfButton @click="register" class="mt-6">Register</SfButton>
      </div>
    </div>
    <Footer />
  </div>
</template>

<script setup>
import Header from '~/components/Header.vue';
import Footer from '~/components/Footer.vue';
import { SfInput, SfButton } from '@storefront-ui/vue';

const user = {
  name: '',
  email: '',
  password: '',
};

function register() {
  // Логика регистрации пользователя
  console.log('User registered:', user);
}
</script>
