Давайте создадим страницы для вашего проекта, чтобы отобразить курсы, корзину и процесс оформления заказа. Мы создадим четыре страницы:

1. **`courses/index.vue`**: Список всех курсов.
2. **`courses/[id].vue`**: Страница с подробной информацией о конкретном курсе.
3. **`cart.vue`**: Страница корзины, где пользователь может видеть добавленные курсы.
4. **`checkout.vue`**: Страница оформления заказа.

### 1. `courses/index.vue` — Список всех курсов

Эта страница будет отображать все доступные курсы в виде карточек.

```vue
<!-- pages/courses/index.vue -->
<template>
  <div class="container mx-auto p-4">
    <h1 class="text-3xl font-bold mb-6">All Courses</h1>
    
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      <CourseCard
        v-for="course in courses"
        :key="course.id"
        :course="course"
      />
    </div>
  </div>
</template>

<script setup>
import CourseCard from '~/components/CourseCard.vue';

// Пример данных курсов
const courses = [
  { id: 1, title: 'Vue 3 and Nuxt 3 Complete Course', instructor: 'John Doe', price: 29.99, image: 'https://via.placeholder.com/150' },
  { id: 2, title: 'Tailwind CSS Mastery', instructor: 'Jane Smith', price: 19.99, image: 'https://via.placeholder.com/150' },
  { id: 3, title: 'JavaScript for Beginners', instructor: 'Alex Johnson', price: 39.99, image: 'https://via.placeholder.com/150' },
  // Добавьте больше курсов по мере необходимости
];
</script>

<style scoped>
/* Добавьте дополнительные стили, если нужно */
</style>
```

### 2. `courses/[id].vue` — Страница подробной информации о курсе

Эта страница будет отображать подробную информацию о конкретном курсе, включая его описание, содержание и кнопку для добавления в корзину.

```vue
<!-- pages/courses/[id].vue -->
<template>
  <div class="container mx-auto p-4">
    <div class="flex flex-col md:flex-row">
      <!-- Изображение курса -->
      <img :src="course.image" :alt="course.title" class="w-full md:w-1/3 rounded-lg shadow-md mb-4 md:mb-0" />
      
      <!-- Описание курса -->
      <div class="md:ml-6">
        <h1 class="text-3xl font-bold mb-2">{{ course.title }}</h1>
        <p class="text-gray-700 mb-4">Instructor: {{ course.instructor }}</p>
        <p class="text-lg font-bold mb-4">{{ course.price }} $</p>
        <p class="text-gray-600 mb-4">{{ course.description }}</p>
        
        <!-- Кнопка добавления в корзину -->
        <SfButton class="bg-green-600 text-white px-4 py-2" @click="addToCart">
          Add to Cart
        </SfButton>
      </div>
    </div>
  </div>
</template>

<script setup>
import { SfButton } from '@storefront-ui/vue';
import { useCartStore } from '~/stores/cart';

// Получаем ID курса из маршрута
const route = useRoute();
const courseId = route.params.id;

// Пример данных курсов (в реальном приложении данные будут загружаться с сервера)
const courses = [
  { id: 1, title: 'Vue 3 and Nuxt 3 Complete Course', instructor: 'John Doe', price: 29.99, image: 'https://via.placeholder.com/150', description: 'Learn Vue 3 and Nuxt 3 from scratch.' },
  { id: 2, title: 'Tailwind CSS Mastery', instructor: 'Jane Smith', price: 19.99, image: 'https://via.placeholder.com/150', description: 'Master Tailwind CSS in this comprehensive course.' },
  { id: 3, title: 'JavaScript for Beginners', instructor: 'Alex Johnson', price: 39.99, image: 'https://via.placeholder.com/150', description: 'An introductory course to JavaScript.' },
  // Добавьте больше курсов по мере необходимости
];

// Ищем курс по ID
const course = courses.find(c => c.id == courseId);

// Функция добавления курса в корзину
const cartStore = useCartStore();
function addToCart() {
  cartStore.addToCart(course);
  alert('Course added to cart!');
}
</script>

<style scoped>
/* Добавьте дополнительные стили, если нужно */
</style>
```

### 3. `cart.vue` — Страница корзины

На этой странице пользователь может увидеть все курсы, добавленные в корзину, удалить их или перейти к оформлению заказа.

```vue
<!-- pages/cart.vue -->
<template>
  <div class="container mx-auto p-4">
    <h1 class="text-2xl font-bold mb-4">Shopping Cart</h1>
    
    <div v-if="cartItems.length === 0">
      <p>Your cart is empty.</p>
    </div>

    <div v-else>
      <!-- Список товаров в корзине -->
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

      <!-- Общая стоимость -->
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

// Получаем данные из состояния корзины
const cartStore = useCartStore();
const cartItems = cartStore.items;
const totalPrice = computed(() => {
  return cartItems.reduce((total, item) => total + item.price, 0);
});

// Функция удаления товара из корзины
function removeFromCart(itemId) {
  cartStore.removeFromCart(itemId);
}

// Функция перехода к оформлению заказа
function proceedToCheckout() {
  // В реальном приложении здесь можно использовать роутер для перехода на страницу оформления заказа
  alert('Proceeding to checkout...');
}
</script>

<style scoped>
/* Добавьте дополнительные стили, если нужно */
</style>
```

### 4. `checkout.vue` — Страница оформления заказа

На этой странице пользователь завершает оформление заказа, вводя свои данные и выбирая способ оплаты.

```vue
<!-- pages/checkout.vue -->
<template>
  <div class="container mx-auto p-4">
    <h1 class="text-2xl font-bold mb-6">Checkout</h1>
    
    <form @submit.prevent="submitOrder">
      <!-- Ввод имени -->
      <div class="mb-4">
        <label class="block text-gray-700">Full Name</label>
        <SfInput v-model="fullName" placeholder="Enter your full name" class="w-full" />
      </div>
      
      <!-- Ввод email -->
      <div class="mb-4">
        <label class="block text-gray-700">Email</label>
        <SfInput v-model="email" type="email" placeholder="Enter your email" class="w-full" />
      </div>
      
      <!-- Выбор способа оплаты -->
      <div class="mb-4">
        <label class="block text-gray-700">Payment Method</label>
        <select v-model="paymentMethod" class="w-full border-gray-300 rounded-md">
          <option value="credit_card">Credit Card</option>
          <option value="paypal">PayPal</option>
          <!-- Добавьте больше опций при необходимости -->
        </select>
      </div>

      <!-- Кнопка подтверждения заказа -->
      <SfButton type="submit" class="bg-blue-600 text-white px-4 py-2 mt-4">
        Place Order
      </SfButton>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { SfButton, SfInput } from '@storefront-ui/vue';

// Состояние формы
const fullName = ref('');
const email = ref('');
const paymentMethod = ref('credit_card');

// Функция обработки отправки формы
function submitOrder() {
  // Здесь должна быть логика обработки заказа (например, вызов API)
  alert(`Order placed! Name: ${fullName.value}, Email: ${email.value

}, Payment Method: ${paymentMethod.value}`);
}
</script>

<style scoped>
/* Добавьте дополнительные стили, если нужно */
</style>
```


Отлично! Давайте последовательно реализуем остальные страницы и компоненты для вашего EdTech проекта. Мы начнем с наиболее важных страниц и компонентов, которые обеспечат полноценную функциональность для MVP вашей платформы.

### 1. Главная страница (`index.vue`)

**Главная страница** будет первым местом, куда попадает пользователь. Она должна отображать популярные курсы, категории курсов и предоставлять краткий обзор возможностей платформы.

```vue
<!-- pages/index.vue -->
<template>
  <div class="container mx-auto p-4">
    <header class="mb-10">
      <h1 class="text-4xl font-bold mb-4">Welcome to Our EdTech Platform</h1>
      <p class="text-lg text-gray-600">Learn from the best instructors in the world.</p>
    </header>

    <!-- Популярные курсы -->
    <section class="mb-10">
      <h2 class="text-2xl font-bold mb-4">Popular Courses</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        <CourseCard
          v-for="course in popularCourses"
          :key="course.id"
          :course="course"
        />
      </div>
    </section>

    <!-- Категории курсов -->
    <section>
      <h2 class="text-2xl font-bold mb-4">Explore Categories</h2>
      <div class="flex flex-wrap gap-4">
        <CategoryCard
          v-for="category in categories"
          :key="category.id"
          :category="category"
        />
      </div>
    </section>
  </div>
</template>

<script setup>
import CourseCard from '~/components/CourseCard.vue';
import CategoryCard from '~/components/CategoryCard.vue';

// Пример данных популярных курсов
const popularCourses = [
  { id: 1, title: 'Vue 3 and Nuxt 3 Complete Course', instructor: 'John Doe', price: 29.99, image: 'https://via.placeholder.com/150' },
  { id: 2, title: 'Tailwind CSS Mastery', instructor: 'Jane Smith', price: 19.99, image: 'https://via.placeholder.com/150' },
  { id: 3, title: 'JavaScript for Beginners', instructor: 'Alex Johnson', price: 39.99, image: 'https://via.placeholder.com/150' },
];

// Пример данных категорий курсов
const categories = [
  { id: 1, name: 'Web Development', image: 'https://via.placeholder.com/150' },
  { id: 2, name: 'Data Science', image: 'https://via.placeholder.com/150' },
  { id: 3, name: 'Business', image: 'https://via.placeholder.com/150' },
  // Добавьте больше категорий по мере необходимости
];
</script>

<style scoped>
/* Дополнительные стили */
</style>
```

### 2. Страница профиля пользователя (`profile.vue`)

**Страница профиля пользователя** позволяет пользователю видеть свои личные данные, а также список курсов, которые он приобрел или которые сейчас проходит.

```vue
<!-- pages/profile.vue -->
<template>
  <div class="container mx-auto p-4">
    <h1 class="text-2xl font-bold mb-6">Profile</h1>
    
    <!-- Информация о пользователе -->
    <section class="mb-8">
      <h2 class="text-xl font-semibold mb-2">Personal Information</h2>
      <p><strong>Name:</strong> {{ user.name }}</p>
      <p><strong>Email:</strong> {{ user.email }}</p>
      <SfButton class="bg-blue-600 text-white px-4 py-2 mt-4" @click="editProfile">
        Edit Profile
      </SfButton>
    </section>

    <!-- Список приобретенных курсов -->
    <section>
      <h2 class="text-xl font-semibold mb-4">My Courses</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        <CourseCard
          v-for="course in myCourses"
          :key="course.id"
          :course="course"
        />
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { SfButton } from '@storefront-ui/vue';
import CourseCard from '~/components/CourseCard.vue';

// Пример данных пользователя
const user = ref({
  name: 'John Doe',
  email: 'john.doe@example.com',
});

// Пример данных курсов пользователя
const myCourses = ref([
  { id: 1, title: 'Vue 3 and Nuxt 3 Complete Course', instructor: 'John Doe', price: 29.99, image: 'https://via.placeholder.com/150' },
  { id: 2, title: 'Tailwind CSS Mastery', instructor: 'Jane Smith', price: 19.99, image: 'https://via.placeholder.com/150' },
]);

function editProfile() {
  alert('Edit Profile functionality coming soon!');
}
</script>

<style scoped>
/* Дополнительные стили */
</style>
```

### 3. Страница логина (`login.vue`)

**Страница логина** позволяет пользователям войти на платформу.

```vue
<!-- pages/login.vue -->
<template>
  <div class="container mx-auto p-4 max-w-md">
    <h1 class="text-2xl font-bold mb-6">Login</h1>
    
    <form @submit.prevent="login">
      <!-- Ввод email -->
      <div class="mb-4">
        <label class="block text-gray-700">Email</label>
        <SfInput v-model="email" type="email" placeholder="Enter your email" class="w-full" />
      </div>
      
      <!-- Ввод пароля -->
      <div class="mb-4">
        <label class="block text-gray-700">Password</label>
        <SfInput v-model="password" type="password" placeholder="Enter your password" class="w-full" />
      </div>

      <!-- Кнопка входа -->
      <SfButton type="submit" class="bg-blue-600 text-white px-4 py-2 mt-4">
        Login
      </SfButton>
    </form>

    <!-- Ссылка на регистрацию -->
    <p class="mt-4">
      Don't have an account? <nuxt-link to="/register" class="text-blue-600">Register here</nuxt-link>.
    </p>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { SfButton, SfInput } from '@storefront-ui/vue';

const email = ref('');
const password = ref('');

function login() {
  // Логика авторизации
  alert(`Logging in with Email: ${email.value}`);
}
</script>

<style scoped>
/* Дополнительные стили */
</style>
```

### 4. Страница регистрации (`register.vue`)

**Страница регистрации** позволяет новым пользователям создать аккаунт.

```vue
<!-- pages/register.vue -->
<template>
  <div class="container mx-auto p-4 max-w-md">
    <h1 class="text-2xl font-bold mb-6">Register</h1>
    
    <form @submit.prevent="register">
      <!-- Ввод имени -->
      <div class="mb-4">
        <label class="block text-gray-700">Full Name</label>
        <SfInput v-model="fullName" placeholder="Enter your full name" class="w-full" />
      </div>
      
      <!-- Ввод email -->
      <div class="mb-4">
        <label class="block text-gray-700">Email</label>
        <SfInput v-model="email" type="email" placeholder="Enter your email" class="w-full" />
      </div>
      
      <!-- Ввод пароля -->
      <div class="mb-4">
        <label class="block text-gray-700">Password</label>
        <SfInput v-model="password" type="password" placeholder="Enter your password" class="w-full" />
      </div>

      <!-- Кнопка регистрации -->
      <SfButton type="submit" class="bg-green-600 text-white px-4 py-2 mt-4">
        Register
      </SfButton>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { SfButton, SfInput } from '@storefront-ui/vue';

const fullName = ref('');
const email = ref('');
const password = ref('');

function register() {
  // Логика регистрации
  alert(`Registering user: ${fullName.value}`);
}
</script>

<style scoped>
/* Дополнительные стили */
</style>
```

### 5. Страница управления курсами для инструкторов (`instructor/courses.vue`)

**Страница управления курсами** позволяет инструкторам видеть свои курсы и управлять ими.

```vue
<!-- pages/instructor/courses.vue -->
<template>
  <div class="container mx-auto p-4">
    <h1 class="text-2xl font-bold mb-6">Manage Your Courses</h1>
    
    <SfButton class="bg-green-600 text-white px-4 py-2 mb-4" @click

="createCourse">
      Create New Course
    </SfButton>
    
    <!-- Список курсов инструктора -->
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      <CourseCard
        v-for="course in instructorCourses"
        :key="course.id"
        :course="course"
      />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { SfButton } from '@storefront-ui/vue';
import CourseCard from '~/components/CourseCard.vue';

// Пример данных курсов инструктора
const instructorCourses = ref([
  { id: 1, title: 'Vue 3 and Nuxt 3 Complete Course', instructor: 'John Doe', price: 29.99, image: 'https://via.placeholder.com/150' },
  { id: 2, title: 'Advanced JavaScript Techniques', instructor: 'John Doe', price: 49.99, image: 'https://via.placeholder.com/150' },
]);

function createCourse() {
  alert('Course creation functionality coming soon!');
}
</script>

<style scoped>
/* Дополнительные стили */
</style>
```

### 6. Страница создания/редактирования курса (`instructor/edit-course.vue`)

**Страница создания/редактирования курса** предоставляет инструктору интерфейс для добавления или редактирования курсов.

```vue
<!-- pages/instructor/edit-course.vue -->
<template>
  <div class="container mx-auto p-4">
    <h1 class="text-2xl font-bold mb-6">{{ isEditing ? 'Edit Course' : 'Create New Course' }}</h1>
    
    <form @submit.prevent="saveCourse">
      <!-- Название курса -->
      <div class="mb-4">
        <label class="block text-gray-700">Course Title</label>
        <SfInput v-model="course.title" placeholder="Enter course title" class="w-full" />
      </div>

      <!-- Описание курса -->
      <div class="mb-4">
        <label class="block text-gray-700">Course Description</label>
        <SfTextarea v-model="course.description" placeholder="Enter course description" class="w-full" />
      </div>

      <!-- Цена курса -->
      <div class="mb-4">
        <label class="block text-gray-700">Price</label>
        <SfInput v-model="course.price" type="number" placeholder="Enter course price" class="w-full" />
      </div>

      <!-- Загрузка видео -->
      <div class="mb-4">
        <label class="block text-gray-700">Upload Course Video</label>
        <FileUpload v-model="course.video" />
      </div>

      <!-- Кнопка сохранения -->
      <SfButton type="submit" class="bg-blue-600 text-white px-4 py-2">
        {{ isEditing ? 'Save Changes' : 'Create Course' }}
      </SfButton>
    </form>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import { SfButton, SfInput, SfTextarea } from '@storefront-ui/vue';
import FileUpload from '~/components/FileUpload.vue';

// Определяем редактирование или создание нового курса
const isEditing = computed(() => !!courseId);
const courseId = ref(null); // Замените реальным идентификатором, если редактирование

const course = ref({
  title: '',
  description: '',
  price: 0,
  video: null,
});

function saveCourse() {
  // Логика сохранения курса
  alert(`Course ${isEditing.value ? 'updated' : 'created'}: ${course.value.title}`);
}
</script>

<style scoped>
/* Дополнительные стили */
</style>
```


