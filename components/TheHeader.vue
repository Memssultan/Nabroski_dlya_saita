<template>
    <header class="bg-white shadow-sm sticky top-0 z-10">
      <nav class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-4">
        <div class="flex justify-between items-center">
          <div class="flex items-center">
            <NuxtLink to="/" class="text-2xl font-bold text-gray-900">КухонныеНожи.рф</NuxtLink>
            <div class="hidden sm:ml-6 sm:flex sm:space-x-8">
              <NuxtLink to="/" class="text-gray-900 inline-flex items-center px-1 pt-1 border-b-2 border-indigo-500 text-sm font-medium">
                Главная
              </NuxtLink>
              <NuxtLink to="/catalog" class="text-gray-500 hover:text-gray-700 inline-flex items-center px-1 pt-1 border-b-2 border-transparent text-sm font-medium">
                Каталог
              </NuxtLink>
              <NuxtLink to="/about" class="text-gray-500 hover:text-gray-700 inline-flex items-center px-1 pt-1 border-b-2 border-transparent text-sm font-medium">
                О нас
              </NuxtLink>
              <NuxtLink to="/contact" class="text-gray-500 hover:text-gray-700 inline-flex items-center px-1 pt-1 border-b-2 border-transparent text-sm font-medium">
                Контакты
              </NuxtLink>
            </div>
          </div>
          <div class="flex items-center">
            <button class="bg-indigo-600 p-1 rounded-full text-white hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
              <span class="sr-only">Корзина</span>
              <svg class="h-6 w-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" aria-hidden="true">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z" />
              </svg>
            </button>
            <span class="ml-2 text-sm font-medium text-gray-700">{{ cartItemsCount }}</span>
          </div>
        </div>
      </nav>
    </header>
  </template>
  
  <script setup>
  defineProps({
    cartItemsCount: {
      type: Number,
      default: 0
    }
  })
  </script>