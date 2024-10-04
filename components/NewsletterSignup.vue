<template>
    <section class="bg-gray-100 py-12 px-4 sm:px-6 lg:px-8 mt-12">
      <div class="max-w-3xl mx-auto text-center">
        <h2 class="text-3xl font-extrabold text-gray-900 sm:text-4xl">
          Подпишитесь на наши новости
        </h2>
        <p class="mt-4 text-lg text-gray-600">
          Получайте эксклюзивные предложения и новости о наших продуктах
        </p>
        <form @submit.prevent="submitForm" class="mt-8 sm:flex justify-center">
          <label for="email-address" class="sr-only">Email address</label>
          <input
            id="email-address"
            name="email"
            type="email"
            autocomplete="email"
            required
            v-model="email"
            class="w-full px-5 py-3 border border-gray-300 shadow-sm placeholder-gray-400 focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500 sm:max-w-xs rounded-md"
            placeholder="Введите ваш email"
          />
          <div class="mt-3 rounded-md shadow sm:mt-0 sm:ml-3 sm:flex-shrink-0">
            <button
              type="submit"
              class="w-full flex items-center justify-center px-5 py-3 border border-transparent text-base font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
            >
              Подписаться
            </button>
          </div>
        </form>
      </div>
    </section>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  const email = ref('')
  
  const submitForm = () => {
    // Здесь будет логика отправки формы
    console.log('Email для подписки:', email.value)
    email.value = ''
  }
  </script>