<template>
  <div class="checkout-page">
    <Header />
    <div class="container mx-auto p-6">
      <h1 class="text-2xl font-bold mb-4">Checkout</h1>
      <div class="bg-white p-6 rounded-lg shadow-md">
        <h2 class="text-lg font-bold mb-4">Billing Information</h2>
        <SfInput v-model="billingInfo.name" placeholder="Full Name" />
        <SfInput v-model="billingInfo.email" placeholder="Email Address" class="mt-4" />
        <SfButton @click="completePurchase" class="mt-6">Complete Purchase</SfButton>
      </div>
    </div>
    <Footer />
  </div>
</template>

<script setup>
import Header from '~/components/Header.vue';
import Footer from '~/components/Footer.vue';
import { SfInput, SfButton } from '@storefront-ui/vue';

const billingInfo = {
  name: '',
  email: '',
};

function completePurchase() {
  // Логика завершения покупки
  console.log('Purchase completed:', billingInfo);
}
</script>
