<template>
    <section class="mb-12">
      <h2 class="text-2xl font-extrabold text-gray-900 mb-6">Категории ножей</h2>
      <div class="grid grid-cols-2 sm:grid-cols-4 gap-4">
        <div v-for="category in categories" :key="category.id" class="relative group">
          <div class="aspect-w-1 aspect-h-1 rounded-lg overflow-hidden bg-gray-100">
            <img :src="category.image" :alt="category.name" class="object-center object-cover group-hover:opacity-75 transition duration-300" />
          </div>
          <h3 class="mt-2 text-sm text-gray-700">
            <NuxtLink :to="`/category/${category.id}`">
              <span class="absolute inset-0"></span>
              {{ category.name }}
            </NuxtLink>
          </h3>
        </div>
      </div>
    </section>
  </template>
  
  <script setup>
  defineProps({
    categories: {
      type: Array,
      required: true
    }
  })
  </script>