<template>
    <div class="min-h-screen bg-gray-100">
      <TheHeader :cartItemsCount="cartItems" />
      
      <main class="max-w-7xl mx-auto py-6 sm:px-6 lg:px-8">
        <div class="px-4 py-6 sm:px-0">
          <h1 class="text-3xl font-bold text-gray-900 mb-6">Контакты</h1>
          
          <div class="bg-white shadow overflow-hidden sm:rounded-lg">
            <div class="px-4 py-5 sm:p-6">
              <div class="grid grid-cols-1 gap-y-6 sm:grid-cols-2 sm:gap-x-8">
                <div>
                  <h2 class="text-2xl font-medium text-gray-900">Свяжитесь с нами</h2>
                  <p class="mt-3 text-lg text-gray-500">
                    У вас есть вопросы или предложения? Мы всегда рады помочь!
                  </p>
                  <dl class="mt-8 text-base text-gray-500">
                    <div>
                      <dt class="sr-only">Адрес</dt>
                      <dd class="flex">
                        <svg class="flex-shrink-0 h-6 w-6 text-gray-400" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" aria-hidden="true">
                          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
                          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
                        </svg>
                        <span class="ml-3">
                          ул. Ножевая, д. 1,<br>
                          Москва, 123456
                        </span>
                      </dd>
                    </div>
                    <div class="mt-6">
                      <dt class="sr-only">Телефон</dt>
                      <dd class="flex">
                        <svg class="flex-shrink-0 h-6 w-6 text-gray-400" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" aria-hidden="true">
                          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
                        </svg>
                        <span class="ml-3">
                          +7 (495) 123-45-67
                        </span>
                      </dd>
                    </div>
                    <div class="mt-3">
                      <dt class="sr-only">Email</dt>
                      <dd class="flex">
                        <svg class="flex-shrink-0 h-6 w-6 text-gray-400" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" aria-hidden="true">
                          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
                        </svg>
                        <span class="ml-3">
                          info@кухонныеножи.рф
                        </span>
                      </dd>
                    </div>
                  </dl>
                </div>
                <div>
                  <h2 class="text-2xl font-medium text-gray-900">Напишите нам</h2>
                  <form @submit.prevent="submitForm" class="mt-6 grid grid-cols-1 gap-y-6 sm:grid-cols-2 sm:gap-x-8">
                    <div>
                      <label for="first-name" class="block text-sm font-medium text-gray-700">Имя</label>
                      <div class="mt-1">
                        <input type="text" name="first-name" id="first-name" autocomplete="given-name" v-model="form.firstName" class="py-3 px-4 block w-full shadow-sm focus:ring-indigo-500 focus:border-indigo-500 border-gray-300 rounded-md">
                      </div>
                    </div>
                    <div>
                      <label for="last-name" class="block text-sm font-medium text-gray-700">Фамилия</label>
                      <div class="mt-1">
                        <input type="text" name="last-name" id="last-name" autocomplete="family-name" v-model="form.lastName" class="py-3 px-4 block w-full shadow-sm focus:ring-indigo-500 focus:border-indigo-500 border-gray-300 rounded-md">
                      </div>
                    </div>
                    <div class="sm:col-span-2">
                      <label for="email" class="block text-sm font-medium text-gray-700">Email</label>
                      <div class="mt-1">
                        <input id="email" name="email" type="email" autocomplete="email" v-model="form.email" class="py-3 px-4 block w-full shadow-sm focus:ring-indigo-500 focus:border-indigo-500 border-gray-300 rounded-md">
                      </div>
                    </div>
                    <div class="sm:col-span-2">
                      <label for="message" class="block text-sm font-medium text-gray-700">Сообщение</label>
                      <div class="mt-1">
                        <textarea id="message" name="message" rows="4" v-model="form.message" class="py-3 px-4 block w-full shadow-sm focus:ring-indigo-500 focus:border-indigo-500 border-gray-300 rounded-md"></textarea>
                      </div>
                    </div>
                    <div class="sm:col-span-2">
                      <button type="submit" class="w-full inline-flex items-center justify-center px-6 py-3 border border-transparent rounded-md shadow-sm text-base font-medium text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                        Отправить
                      </button>
                    </div>
                  </form>
                </div>
              </div>
            </div>
          </div>
        </div>
      </main>
  
      <TheFooter />
    </div>
  </template>
  
  <script setup>
  import { ref, reactive } from 'vue'
  import TheHeader from '~/components/TheHeader.vue'
  import TheFooter from '~/components/TheFooter.vue'
  
  const cartItems = ref(0)
  
  const form = reactive({
    firstName: '',
    lastName: '',
    email: '',
    message: ''
  })
  
  const submitForm = () => {
    // Здесь будет логика отправки формы
    console.log('Форма отправлена:', form)
    // Очистка формы после отправки
    Object.keys(form).forEach(key => form[key] = '')
  }
  </script>