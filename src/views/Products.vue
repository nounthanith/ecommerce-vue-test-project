<script setup lang="ts">
import { ref, onMounted } from 'vue'
import Carousel from '../features/Carousel.vue'
import ProductCard from '../components/ProductCard.vue'
import ProductCardLoader from '../components/ProductCardLoader.vue'

interface Product {
  id: number
  name: string
  price: number
  category: string
  image: string
}

const isLoading = ref(true)
const products = ref<Product[]>([])

onMounted(() => {
  // Simulate API loading
  setTimeout(() => {
    products.value = [
      {
        id: 1,
        name: 'Minimalist Chair',
        price: 99.99,
        category: 'Furniture',
        image: 'https://picsum.photos/seed/1/800/800'
      },
      {
        id: 2,
        name: 'Glass Vase',
        price: 149.99,
        category: 'Decor',
        image: 'https://picsum.photos/seed/2/800/800'
      },
      {
        id: 3,
        name: 'Hot Pink Lamp',
        price: 199.99,
        category: 'Lighting',
        image: 'https://picsum.photos/seed/3/800/800'
      },
      {
        id: 4,
        name: 'Cotton Pillow',
        price: 79.99,
        category: 'Textiles',
        image: 'https://picsum.photos/seed/4/800/800'
      },
      {
        id: 5,
        name: 'Ceramic Plate',
        price: 129.99,
        category: 'Kitchen',
        image: 'https://picsum.photos/seed/5/800/800'
      }
    ]

    isLoading.value = false
  }, 2000)
})
</script>

<template>
  <div class="min-h-screen bg-gradient-to-b from-white via-gray-50 to-white">

    <!-- HERO / CAROUSEL -->
    <Carousel />

    <!-- SECTION HEADER -->
    <div class="pt-24 pb-12 px-6 md:px-12 max-w-7xl mx-auto">
      <div class="flex items-end justify-between gap-6">

        <div>
          <span
            class="text-[#FF1493] text-[11px] font-extrabold
                   uppercase tracking-[0.35em]"
          >
            New Season
          </span>

          <h2
            class="mt-2 text-3xl sm:text-4xl md:text-5xl
                   font-black italic uppercase tracking-tight
                   text-gray-900 leading-none"
          >
            Featured Products
          </h2>

          <p class="mt-3 max-w-md text-sm text-gray-500">
            Hand-picked pieces designed to elevate your everyday living.
          </p>
        </div>

        <a
          href="#"
          class="hidden sm:flex items-center gap-2
                 text-xs font-bold uppercase tracking-widest
                 text-gray-400 hover:text-[#FF1493]
                 transition-colors group"
        >
          View All
          <span class="group-hover:translate-x-1 transition-transform">→</span>
        </a>

      </div>
    </div>

    <!-- PRODUCTS RAIL -->
    <div class="relative w-full overflow-hidden">
      <div
        class="flex gap-6 md:gap-8 overflow-x-auto snap-x snap-mandatory
               px-6 md:px-12 pb-24 no-scrollbar scroll-smooth"
      >

        <!-- LOADING STATE -->
        <template v-if="isLoading">
          <div
            v-for="i in 10"
            :key="i"
            class="w-[260px] sm:w-[280px] md:w-[320px]
                   shrink-0 snap-start"
          >
            <ProductCardLoader />
          </div>
        </template>

        <!-- PRODUCTS -->
        <template v-else>
          <div
            v-for="product in products"
            :key="product.id"
            class="group w-[260px] sm:w-[280px] md:w-[320px]
                   shrink-0 snap-start
                   transition-transform duration-300
                   hover:-translate-y-2"
          >
            <ProductCard
              :product="product"
              class="animate-fade-in"
            />
          </div>

          <!-- END SPACING -->
          <div class="w-16 shrink-0"></div>
        </template>

      </div>
    </div>

  </div>
</template>

<style scoped>
/* Hide scrollbar but keep swipe */
.no-scrollbar::-webkit-scrollbar {
  display: none;
}
.no-scrollbar {
  -ms-overflow-style: none;
  scrollbar-width: none;
}

/* Fade-in animation */
@keyframes fade-in {
  from {
    opacity: 0;
    transform: translateY(12px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fade-in {
  animation: fade-in 0.6s ease-out both;
}
</style>