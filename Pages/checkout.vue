<!-- pages/checkout.vue -->
<template>
    <div class="container mx-auto p-4">
      <h1 class="text-2xl font-bold mb-6">Checkout</h1>
      
      <form @submit.prevent="submitOrder">
        <!-- Enter name -->
        <div class="mb-4">
          <label class="block text-gray-700">Full Name</label>
          <SfInput v-model="fullName" placeholder="Enter your full name" class="w-full" />
        </div>
        
        <!-- Enter email -->
        <div class="mb-4">
          <label class="block text-gray-700">Email</label>
          <SfInput v-model="email" type="email" placeholder="Enter your email" class="w-full" />
        </div>
        
        <!-- Payments methods -->
        <div class="mb-4">
          <label class="block text-gray-700">Payment Method</label>
          <select v-model="paymentMethod" class="w-full border-gray-300 rounded-md">
            <option value="credit_card">Credit Card</option>
            <option value="paypal">PayPal</option>
            <!-- Add more options if needed -->
          </select>
        </div>
  
        <!-- Submit order button -->
        <SfButton type="submit" class="bg-blue-600 text-white px-4 py-2 mt-4">
          Place Order
        </SfButton>
      </form>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  import { SfButton, SfInput } from '@storefront-ui/vue';
  
  // Form process
  const fullName = ref('');
  const email = ref('');
  const paymentMethod = ref('credit_card');
  
  // Form sending function
  function submitOrder() {
    // Order transacrtion logics (Call API)
    alert(`Order placed! Name: ${fullName.value}, Email: ${email.value}, Payment Method: ${paymentMethod.value}`);
  }
  </script>
  
  <style scoped>
  /* Styles */
  </style>
  