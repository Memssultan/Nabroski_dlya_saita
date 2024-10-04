<template>
    <div class="min-h-screen bg-gray-50">
      <TheHeader :cartItemsCount="cartItems" />
      
      <main class="max-w-7xl mx-auto py-6 sm:px-6 lg:px-8">
        <FeaturedProducts :products="featuredProducts" @add-to-cart="addToCart" />
        
        <ProductCategories :categories="categories" />
        
        <ProductList 
          :products="products" 
          @add-to-cart="addToCart"
          @quick-view="openQuickView"
        />
        
        <NewsletterSignup />
      </main>
  
      <TheFooter />
  
      <QuickViewModal 
        v-if="quickViewProduct" 
        :product="quickViewProduct" 
        @close="closeQuickView"
        @add-to-cart="addToCart"
      />
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  import TheHeader from '~/components/TheHeader.vue'
  import FeaturedProducts from '~/components/FeaturedProduct.vue'
  import ProductCategories from '~/components/ProductCategories.vue'
  import ProductList from '~/components/ProductList.vue'
  import NewsletterSignup from '~/components/NewsletterSignup.vue'
  import TheFooter from '~/components/TheFooter.vue'
  import QuickViewModal from '~/components/QuickViewModal.vue'
  
  const cartItems = ref(0)
  const quickViewProduct = ref(null)
  
  const addToCart = (product) => {
    cartItems.value++
    // В реальном приложении здесь бы добавлялся товар в корзину
    console.log(`Добавлен товар: ${product.name}`)
  }
  
  const openQuickView = (product) => {
    quickViewProduct.value = product
  }
  
  const closeQuickView = () => {
    quickViewProduct.value = null
  }
  
  const featuredProducts = [
    {
      id: 1,
      name: "Шеф-нож Премиум",
      description: "Профессиональный шеф-нож из дамасской стали. Идеален для нарезки мяса, овощей и фруктов.",
      price: 15999,
      rating: 4.9,
      reviews: 128,
      image: "https://images.unsplash.com/photo-1593618998160-e34014e67546?auto=format&fit=crop&q=80&w=1000"
    },
    {
      id: 2,
      name: "Сантоку Элит",
      description: "Универсальный японский нож для нарезки, шинковки и рубки.",
      price: 12999,
      rating: 4.8,
      reviews: 95,
      image: "https://images.unsplash.com/photo-1592154014052-2f2a0b9b1a79?auto=format&fit=crop&q=80&w=1000"
    },
    {
      id: 3,
      name: "Нож для филе Профи",
      description: "Гибкий и острый нож для идеального филетирования рыбы и мяса.",
      price: 8999,
      rating: 4.7,
      reviews: 76,
      image: "https://images.unsplash.com/photo-1591349341536-d0b9a5d2b7b5?auto=format&fit=crop&q=80&w=1000"
    }
  ]
  
  const categories = [
    { id: 1, name: 'Шеф-ножи', image: 'https://images.unsplash.com/photo-1593618998160-e34014e67546?auto=format&fit=crop&q=80&w=300' },
    { id: 2, name: 'Ножи для овощей', image: 'https://images.unsplash.com/photo-1608877907149-a206d75ba011?auto=format&fit=crop&q=80&w=300' },
    { id: 3, name: 'Ножи для мяса', image: 'https://images.unsplash.com/photo-1614981226683-2625ba2d5c09?auto=format&fit=crop&q=80&w=300' },
    { id: 4, name: 'Ножи для хлеба', image: 'https://images.unsplash.com/photo-1591349341536-d0b9a5d2b7b5?auto=format&fit=crop&q=80&w=300' },
  ]
  
  const products = [
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
    {
      id: 4,
      name: 'Универсальный нож',
      description: 'Многофункциональный нож для различных кухонных задач.',
      price: 4299,
      image: 'https://images.unsplash.com/photo-1593618998160-e34014e67546?auto=format&fit=crop&q=80&w=300'
    },
    {
      id: 5,
      name: 'Сантоку',
      description: 'Японский нож для нарезки, шинковки и рубки.',
      price: 6999,
      image: 'https://images.unsplash.com/photo-1592154014052-2f2a0b9b1a79?auto=format&fit=crop&q=80&w=300'
    },
    {
      id: 6,
      name: 'Нож для чистки',
      description: 'Маленький нож для чистки и подготовки овощей и фруктов.',
      price: 2499,
      image: 'https://images.unsplash.com/photo-1608877907149-a206d75ba011?auto=format&fit=crop&q=80&w=300'
    },
  ]
  </script>