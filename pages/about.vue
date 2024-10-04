<template>
    <div class="min-h-screen bg-gray-100">
      <TheHeader :cartItemsCount="cartItems" />
      
      <main class="max-w-7xl mx-auto py-6 sm:px-6 lg:px-8">
        <div class="px-4 py-6 sm:px-0">
          <h1 class="text-3xl font-bold text-gray-900 mb-6">О нас</h1>
          
          <div class="bg-white shadow overflow-hidden sm:rounded-lg">
            <div class="px-4 py-5 sm:px-6">
              <h2 class="text-2xl leading-6 font-medium text-gray-900">
                КухонныеНожи.рф - Ваш надежный партнер в мире кулинарии
              </h2>
            </div>
            <div class="border-t border-gray-200">
              <dl>
                <div class="bg-gray-50 px-4 py-5 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-6">
                  <dt class="text-sm font-medium text-gray-500">Наша миссия</dt>
                  <dd class="mt-1 text-sm text-gray-900 sm:mt-0 sm:col-span-2">
                    Предоставлять нашим клиентам высококачественные кухонные ножи, которые вдохновляют на кулинарные подвиги и делают процесс приготовления пищи приятным и эффективным.
                  </dd>
                </div>
                <div class="bg-white px-4 py-5 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-6">
                  <dt class="text-sm font-medium text-gray-500">История</dt>
                  <dd class="mt-1 text-sm text-gray-900 sm:mt-0 sm:col-span-2">
                    Основанная в 2010 году, наша компания начала свой путь с небольшого магазина в центре Москвы. За годы работы мы выросли в крупного поставщика кухонных ножей, известного по всей России своим качеством и обслуживанием клиентов.
                  </dd>
                </div>
                <div class="bg-gray-50 px-4 py-5 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-6">
                  <dt class="text-sm font-medium text-gray-500">Наши преимущества</dt>
                  <dd class="mt-1 text-sm text-gray-900 sm:mt-0 sm:col-span-2">
                    <ul class="list-disc pl-5">
                      <li>Широкий ассортимент ножей от ведущих мировых производителей</li>
                      <li>Профессиональная консультация при выборе ножей</li>
                      <li>Гарантия качества на все товары</li>
                      <li>Быстрая доставка по всей России</li>
                      <li>Отличное соотношение цены и качества</li>
                    </ul>
                  </dd>
                </div>
                <div class="bg-white px-4 py-5 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-6">
                  <dt class="text-sm font-medium text-gray-500">Наша команда</dt>
                  <dd class="mt-1 text-sm text-gray-900 sm:mt-0 sm:col-span-2">
                    Мы - команда энтузиастов, объединенных любовью к кулинарии и качественным инструментам. Наши эксперты постоянно следят за новинками рынка и тестируют каждый нож, чтобы предложить вам только лучшее.
                  </dd>
                </div>
              </dl>
            </div>
          </div>
          
          <div class="mt-10">
            <h2 class="text-2xl font-bold text-gray-900 mb-4">Наши партнеры</h2>
            <div class="grid grid-cols-2 gap-8 md:grid-cols-4">
              <div v-for="partner in partners" :key="partner.id" class="col-span-1 flex justify-center items-center">
                <img class="h-12" :src="partner.logo" :alt="partner.name">
              </div>
            </div>
          </div>
        </div>
      </main>
  
      <TheFooter />
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  import TheHeader from '~/components/TheHeader.vue'
  import TheFooter from '~/components/TheFooter.vue'
  
  const cartItems = ref(0)
  
  const partners = [
    { id: 1, name: 'Wüsthof', logo: 'https://via.placeholder.com/150x50.png?text=Wüsthof' },
    { id: 2, name: 'Zwilling', logo: 'https://via.placeholder.com/150x50.png?text=Zwilling' },
    { id: 3, name: 'Global', logo: 'https://via.placeholder.com/150x50.png?text=Global' },
    { id: 4, name: 'Shun', logo: 'https://via.placeholder.com/150x50.png?text=Shun' },
  ]
  </script>