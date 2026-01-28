<script setup lang="ts">
import { ref, onMounted } from 'vue'
import Carousel from '../features/Carousel.vue';
import ProductCard from '../features/ProductCard.vue';

const isLoading = ref(true)
const products = ref([])

onMounted(() => {
  // Simulate loading products
  setTimeout(() => {
    products.value = [
      { id: 1, name: 'Product 1', price: 99.99 },
      { id: 2, name: 'Product 2', price: 149.99 },
      { id: 3, name: 'Product 3', price: 199.99 },
      { id: 4, name: 'Product 4', price: 79.99 },
      { id: 5, name: 'Product 5', price: 129.99 },
    ]
    isLoading.value = false
  }, 2000)
})
</script>

<template>
    <div>
        <Carousel />
        
        <div class="py-16 text-center text-2xl font-bold">Products</div>
        
        <div class="container mx-auto px-6">
            <div class="grid grid-cols-2 sm:grid-cols-2 lg:grid-cols-4 xl:grid-cols-5 gap-8">
                
                <template v-if="isLoading">
                  <ProductCard v-for="i in 20" :key="i" />
                </template>

                <template v-else>
                  <ProductCard v-for="product in products" :key="product.id" :product="product" />
                </template>

            </div>
        </div>
    </div>
</template>