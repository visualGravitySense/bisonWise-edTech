<!-- pages/cart.vue -->
<template>
    <div class="container mx-auto p-4">
      <h1 class="text-2xl font-bold mb-4">Shopping Cart</h1>
      
      <div v-if="cartItems.length === 0">
        <p>Your cart is empty.</p>
      </div>
  
      <div v-else>
        <!-- Products in cart -->
        <ul>
          <li v-for="item in cartItems" :key="item.id" class="mb-4">
            <div class="flex justify-between items-center border-b pb-2">
              <div>
                <h2 class="text-lg">{{ item.title }}</h2>
                <p class="text-gray-600">{{ item.price }} $</p>
              </div>
              <SfButton class="bg-red-500 text-white px-4 py-2" @click="removeFromCart(item.id)">
                Remove
              </SfButton>
            </div>
          </li>
        </ul>
  
        <!-- Main cost -->
        <div class="mt-6">
          <h2 class="text-xl font-bold">Total: {{ totalPrice }} $</h2>
          <SfButton class="bg-green-600 text-white px-4 py-2 mt-4" @click="proceedToCheckout">
            Proceed to Checkout
          </SfButton>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { SfButton } from '@storefront-ui/vue';
  import { useCartStore } from '~/stores/cart';
  
  // Getting data from Cart
  const cartStore = useCartStore();
  const cartItems = cartStore.items;
  const totalPrice = computed(() => {
    return cartItems.reduce((total, item) => total + item.price, 0);
  });
  
  // Delite from cart
  function removeFromCart(itemId) {
    cartStore.removeFromCart(itemId);
  }
  
  // Function to order
  function proceedToCheckout() {
    // Router to order page
    alert('Proceeding to checkout...');
  }
  </script>
  
  <style scoped>
  /*  */
  </style>
  