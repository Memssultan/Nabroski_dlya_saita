<template>
    <div class="min-h-screen bg-gray-100">
      <header class="bg-white shadow-sm">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-4 flex justify-between items-center">
          <h1 class="text-2xl font-bold text-gray-900">Премиум кухонные ножи</h1>
          <button class="relative inline-flex items-center px-4 py-2 border border-transparent text-sm font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z" />
            </svg>
            Корзина
            <span class="absolute -top-1 -right-1 inline-flex items-center justify-center px-2 py-1 text-xs font-bold leading-none text-red-100 bg-red-600 rounded-full">{{ cartItems }}</span>
          </button>
        </div>
      </header>
  
      <main class="max-w-7xl mx-auto py-6 sm:px-6 lg:px-8">
        <section class="mb-12">
          <div class="bg-white shadow overflow-hidden sm:rounded-lg">
            <div class="md:flex">
              <div class="md:w-1/2">
                <img :src="featuredKnife.image" :alt="featuredKnife.name" class="w-full h-full object-cover" />
              </div>
              <div class="md:w-1/2 p-8 flex flex-col justify-center">
                <span class="inline-flex items-center px-3 py-0.5 rounded-full text-sm font-medium bg-indigo-100 text-indigo-800 mb-2">
                  Рекомендуем
                </span>
                <h2 class="text-3xl font-extrabold text-gray-900 mb-2">{{ featuredKnife.name }}</h2>
                <p class="text-gray-500 mb-4">{{ featuredKnife.description }}</p>
                <div class="flex items-center mb-4">
                  <div class="flex items-center">
                    <svg v-for="i in 5" :key="i" :class="[i <= Math.floor(featuredKnife.rating) ? 'text-yellow-400' : 'text-gray-300', 'h-5 w-5']" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
                      <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
                    </svg>
                  </div>
                  <p class="ml-2 text-sm text-gray-600">{{ featuredKnife.rating }} ({{ featuredKnife.reviews }} отзывов)</p>
                </div>
                <p class="text-3xl font-bold text-gray-900 mb-4">{{ formatPrice(featuredKnife.price) }} ₽</p>
                <div class="flex space-x-4">
                  <button @click="addToCart" class="inline-flex items-center px-6 py-3 border border-transparent text-base font-medium rounded-md shadow-sm text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                    Добавить в корзину
                  </button>
                  <button class="inline-flex items-center px-4 py-3 border border-gray-300 shadow-sm text-base font-medium rounded-md text-gray-700 bg-white hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z" />
                    </svg>
                  </button>
                </div>
              </div>
            </div>
          </div>
        </section>
  
        <section>
          <div class="sm:hidden">
            <label for="tabs" class="sr-only">Выберите категорию</label>
            <select id="tabs" name="tabs" class="block w-full pl-3 pr-10 py-2 text-base border-gray-300 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm rounded-md">
              <option v-for="tab in tabs" :key="tab.name" :selected="tab.name === currentTab">{{ tab.name }}</option>
            </select>
          </div>
          <div class="hidden sm:block mb-8">
            <div class="border-b border-gray-200">
              <nav class="-mb-px flex space-x-8" aria-label="Tabs">
                <a v-for="tab in tabs" :key="tab.name" :href="tab.href" @click.prevent="currentTab = tab.name" :class="[tab.name === currentTab ? 'border-indigo-500 text-indigo-600' : 'border-transparent text-gray-500 hover:text-gray-700 hover:border-gray-300', 'whitespace-nowrap py-4 px-1 border-b-2 font-medium text-sm']">
                  {{ tab.name }}
                </a>
              </nav>
            </div>
          </div>
  
          <div class="grid grid-cols-1 gap-y-10 sm:grid-cols-2 gap-x-6 lg:grid-cols-3 xl:gap-x-8">
            <div v-for="knife in knives" :key="knife.id" class="group">
              <div class="w-full aspect-w-1 aspect-h-1 bg-gray-200 rounded-lg overflow-hidden">
                <img :src="knife.image" :alt="knife.name" class="w-full h-full object-center object-cover group-hover:opacity-75" />
              </div>
              <h3 class="mt-4 text-sm text-gray-700">{{ knife.name }}</h3>
              <p class="mt-1 text-lg font-medium text-gray-900">{{ formatPrice(knife.price) }} ₽</p>
              <button @click="addToCart" class="mt-3 w-full bg-indigo-600 border border-transparent rounded-md py-2 px-8 flex items-center justify-center text-sm font-medium text-white hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                В корзину
              </button>
            </div>
          </div>
  
          <div class="mt-8 text-center">
            <button class="inline-flex items-center px-4 py-2 border border-transparent text-sm font-medium rounded-md text-indigo-600 bg-indigo-100 hover:bg-indigo-200 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
              Смотреть все ножи
              <svg xmlns="http://www.w3.org/2000/svg" class="ml-2 h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                <path fill-rule="evenodd" d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z" clip-rule="evenodd" />
              </svg>
            </button>
          </div>
        </section>
      </main>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  const cartItems = ref(0)
  const currentTab = ref('Все ножи')
  
  const addToCart = () => {
    cartItems.value++
  }
  
  const formatPrice = (price) => {
    return price.toLocaleString('ru-RU')
  }
  
  const featuredKnife = {
    name: "Шеф-нож Премиум",
    description: "Профессиональный шеф-нож из дамасской стали. Идеален для нарезки мяса, овощей и фруктов.",
    price: 15999,
    rating: 4.9,
    reviews: 128,
    image: "https://images.unsplash.com/photo-1593618998160-e34014e67546?auto=format&fit=crop&q=80&w=1000"
  }
  
  const knives = [
    {
      id: 1,
      name: 'Нож для овощей',
      description: 'Легкий и острый нож для точной нарезки овощей и фруктов.',
      price: 3999,
      image: 'https://images.unsplash.com/photo-1608877907149-a206d75ba011?auto=format&fit=crop&q=80&w=300'
    },
    {
      id: 2,
      name: 'Нож для хлеба',
      description: 'Нож с зубчатым лезвием для идеальной нарезки хлеба.',
      price: 4499,
      image: 'https://images.unsplash.com/photo-1591349341536-d0b9a5d2b7b5?auto=format&fit=crop&q=80&w=300'
    },
    {
      id: 3,
      name: 'Нож для мяса',
      description: 'Прочный нож для разделки и нарезки мяса.',
      price: 5999,
      image: 'https://images.unsplash.com/photo-1614981226683-2625ba2d5c09?auto=format&fit=crop&q=80&w=300'
    },
  ]
  
  const tabs = [
    { name: 'Все ножи', href: '#' },
    { name: 'Шеф-ножи', href: '#' },
    { name: 'Хлебные ножи', href: '#' },
    { name: 'Универсальные ножи', href: '#' },
  ]
  </script>