<template>
  <div class="cart-page">
    <Header />
    <div class="container mx-auto p-6">
      <h1 class="text-2xl font-bold mb-4">Your Cart</h1>
      <div v-if="cartItems.length">
        <CourseCard v-for="item in cartItems" :key="item.id" :course="item" />
        <SfButton @click="checkout" class="mt-6">Proceed to Checkout</SfButton>
      </div>
      <p v-else>Your cart is empty.</p>
    </div>
    <Footer />
  </div>
</template>

<script setup>
import Header from '~/components/Header.vue';
import Footer from '~/components/Footer.vue';
import CourseCard from '~/components/CourseCard.vue';
import { SfButton } from '@storefront-ui/vue';

// Пример данных корзины
const cartItems = [
  { id: 1, title: 'Vue.js Basics', description: 'Learn the basics of Vue.js', price: '$49', image: 'path/to/image' },
];

function checkout() {
  // Логика перехода на страницу оформления заказа
  console.log('Proceeding to checkout');
}
</script>
