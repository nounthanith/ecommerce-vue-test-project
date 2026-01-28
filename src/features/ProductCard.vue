<template>
  <div class="group relative flex flex-col space-y-4">
    <!-- Loader State -->
    <template v-if="!product">
      <div class="relative aspect-4/5 overflow-hidden rounded-none bg-gray-50 border border-gray-100 flex items-center justify-center">
        
        <span class="relative flex h-12 w-12">
          <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-[#FF1493] opacity-20"></span>
          <span class="relative inline-flex rounded-full h-12 w-12 bg-[#FF1493]/10 border border-[#FF1493]/20"></span>
        </span>

        <div class="absolute inset-0 -translate-x-full bg-linear-to-r from-transparent via-white/60 to-transparent animate-shimmer"></div>
      </div>

      <div class="space-y-3 px-1">
        <div class="h-3 w-2/3 bg-gray-100 rounded-full overflow-hidden relative">
          <div class="absolute inset-0 -translate-x-full bg-linear-to-r from-transparent via-gray-200/50 to-transparent animate-shimmer"></div>
        </div>
        <div class="h-3 w-1/4 bg-gray-50 rounded-full overflow-hidden relative">
          <div class="absolute inset-0 -translate-x-full bg-linear-to-r from-transparent via-gray-200/50 to-transparent animate-shimmer-slow"></div>
        </div>
      </div>
    </template>

    <!-- Product State -->
    <template v-else>
      <div class="relative aspect-4/5 overflow-hidden rounded-none bg-gray-50 border border-gray-100 flex items-center justify-center">
        <!-- <img 
          :src="product.image || '/placeholder-product.jpg'" 
          :alt="product.name"
          class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-300"
        /> -->
      </div>

      <div class="space-y-2 px-1">
        <h3 class="font-medium text-gray-900 group-hover:text-[#FF1493] transition-colors">
          {{ product.name }}
        </h3>
        <p class="text-lg font-bold text-gray-900">
          ${{ product.price }}
        </p>
      </div>
    </template>
  </div>
</template>

<script setup>
defineProps({
  product: {
    type: Object,
    default: null
  }
})
</script>

<style scoped>
@keyframes shimmer {
  0% { transform: translateX(-100%); }
  100% { transform: translateX(100%); }
}

.animate-shimmer {
  animation: shimmer 2s cubic-bezier(0.4, 0, 0.2, 1) infinite;
}

.animate-shimmer-slow {
  animation: shimmer 3s cubic-bezier(0.4, 0, 0.2, 1) infinite;
}

/* Make the ping very soft and modern */
.animate-ping {
  animation: ping 2s cubic-bezier(0, 0, 0.2, 1) infinite;
}

@keyframes ping {
  75%, 100% {
    transform: scale(2.5);
    opacity: 0;
  }
}
</style>