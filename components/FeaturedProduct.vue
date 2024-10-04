<template>
    <section class="mb-12">
      <h2 class="text-2xl font-extrabold text-gray-900 mb-6">Рекомендуемые товары</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        <div v-for="product in products" :key="product.id" class="bg-white shadow-md rounded-lg overflow-hidden">
          <img :src="product.image" :alt="product.name" class="w-full h-48 object-cover" />
          <div class="p-4">
            <h3 class="text-lg font-semibold text-gray-900 mb-2">{{ product.name }}</h3>
            <p class="text-gray-600 mb-4">{{ product.description }}</p>
            <div class="flex items-center justify-between">
              <span class="text-2xl font-bold text-gray-900">{{ formatPrice(product.price) }} ₽</span>
              <button @click="$emit('add-to-cart', product)" class="bg-indigo-600 text-white px-4 py-2 rounded hover:bg-indigo-700 transition duration-300">
                В корзину
              </button>
            </div>
          </div>
        </div>
      </div>
    </section>
  </template>
  
  <script setup>
  defineProps({
    products: {
      type: Array,
      required: true
    }
  })
  
  defineEmits(['add-to-cart'])
  
  const formatPrice = (price) => {
    return price.toLocaleString('ru-RU')
  }
  </script>