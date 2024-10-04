<template>
    <div class="min-h-screen bg-gray-100">
      <TheHeader :cartItemsCount="cartItems" />
      
      <main class="max-w-7xl mx-auto py-6 sm:px-6 lg:px-8">
        <div class="px-4 py-6 sm:px-0">
          <h1 class="text-3xl font-bold text-gray-900 mb-6">Каталог ножей</h1>
          
          <div class="mb-8">
            <label for="category" class="block text-sm font-medium text-gray-700">Категория</label>
            <select id="category" v-model="selectedCategory" class="mt-1 block w-full pl-3 pr-10 py-2 text-base border-gray-300 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm rounded-md">
              <option value="">Все категории</option>
              <option v-for="category in categories" :key="category.id" :value="category.id">
                {{ category.name }}
              </option>
            </select>
          </div>
          
          <div class="grid grid-cols-1 gap-y-10 sm:grid-cols-2 gap-x-6 lg:grid-cols-3 xl:grid-cols-4 xl:gap-x-8">
            <div v-for="product in filteredProducts" :key="product.id" class="group">
              <div class="w-full aspect-w-1 aspect-h-1 bg-gray-200 rounded-lg overflow-hidden xl:aspect-w-7 xl:aspect-h-8">
                <img :src="product.image" :alt="product.name" class="w-full h-full object-center object-cover group-hover:opacity-75">
              </div>
              <h3 class="mt-4 text-sm text-gray-700">{{ product.name }}</h3>
              <p class="mt-1 text-lg font-medium text-gray-900">{{ formatPrice(product.price) }} ₽</p>
              <button @click="addToCart(product)" class="mt-2 w-full bg-indigo-600 border border-transparent rounded-md py-2 px-8 flex items-center justify-center text-sm font-medium text-white hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                В корзину
              </button>
            </div>
          </div>
        </div>
      </main>
  
      <TheFooter />
    </div>
  </template>
  
  <script setup>
  import { ref, computed } from 'vue'
  import TheHeader from '~/components/TheHeader.vue'
  import TheFooter from '~/components/TheFooter.vue'
  
  const cartItems = ref(0)
  const selectedCategory = ref('')
  
  const categories = [
    { id: 1, name: 'Шеф-ножи' },
    { id: 2, name: 'Ножи для овощей' },
    { id: 3, name: 'Ножи для мяса' },
    { id: 4, name: 'Ножи для хлеба' },
  ]
  
  const products = [
    {
      id: 1,
      name: 'Шеф-нож Премиум',
      price: 15999,
      image: 'https://images.unsplash.com/photo-1593618998160-e34014e67546?auto=format&fit=crop&q=80&w=300',
      categoryId: 1
    },
    {
      id: 2,
      name: 'Нож для овощей',
      price: 3999,
      image: 'https://images.unsplash.com/photo-1608877907149-a206d75ba011?auto=format&fit=crop&q=80&w=300',
      categoryId: 2
    },
    {
      id: 3,
      name: 'Нож для мяса',
      price: 5999,
      image: 'https://images.unsplash.com/photo-1614981226683-2625ba2d5c09?auto=format&fit=crop&q=80&w=300',
      categoryId: 3
    },
    {
      id: 4,
      name: 'Нож для хлеба',
      price: 4499,
      image: 'https://images.unsplash.com/photo-1591349341536-d0b9a5d2b7b5?auto=format&fit=crop&q=80&w=300',
      categoryId: 4
    },
    // Добавьте больше продуктов по необходимости
  ]
  
  const filteredProducts = computed(() => {
    if (selectedCategory.value) {
      return products.filter(product => product.categoryId === parseInt(selectedCategory.value))
    }
    return products
  })
  
  const addToCart = (product) => {
    cartItems.value++
    console.log(`Добавлен товар: ${product.name}`)
  }
  
  const formatPrice = (price) => {
    return price.toLocaleString('ru-RU')
  }
  </script>