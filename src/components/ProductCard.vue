<template>
  <div class="group flex flex-col bg-white transition-all duration-300 cursor-pointer">
    <div class="relative aspect-square overflow-hidden rounded-none bg-[#F6F6F6]">
      <img
        :src="product.image"
        :alt="product.name"
        class="h-full w-full object-cover transition-transform duration-700 ease-out group-hover:scale-105"
      />

      <button 
        @click.stop="$emit('add-to-cart', product)"
        class="absolute bottom-3 right-3 flex h-10 w-10 items-center justify-center rounded-full bg-white text-gray-900 shadow-sm transition-all duration-300 hover:bg-[#FF1493] hover:text-white active:scale-90 opacity-0 translate-y-2 group-hover:opacity-100 group-hover:translate-y-0"
      >
        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4" />
        </svg>
      </button>
    </div>

    <div class="mt-4 flex flex-col items-center text-center">
      <span class="text-[10px] font-bold uppercase tracking-[0.2em] text-[#FF1493] mb-1">
        {{ product.category }}
      </span>
      <h3 class="text-sm font-semibold text-gray-800 tracking-tight leading-tight group-hover:text-[#FF1493] transition-colors">
        {{ product.name }}
      </h3>
      <div class="mt-1.5 font-bold text-gray-900">
        ${{ product.price }}
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
defineProps<{
  product: {
    id: number;
    name: string;
    price: number;
    category: string;
    image: string;
  }
}>();

defineEmits(['add-to-cart']);
</script>