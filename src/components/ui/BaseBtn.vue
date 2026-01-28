<template>
  <button
    :type="type"
    class="group relative inline-flex items-center justify-center font-medium transition-all duration-200 active:scale-95"
    :class="[variantClasses, sizeClasses]"
  >
    <slot />
  </button>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  variant: {
    type: String,
    default: 'primary', 
  },
  size: {
    type: String,
    default: 'md',
  },
  type: {
    type: String,
    default: 'button',
  },
})

const variantClasses = computed(() => {
  switch (props.variant) {
    case 'primary':
      return 'bg-[#FF1493] text-white hover:bg-[#E01282] shadow-sm hover:shadow-md'
    case 'outline':
      return 'border border-gray-200 text-gray-700 hover:border-[#FF1493] hover:text-[#FF1493]'
    case 'simple':
      return 'text-gray-500 hover:text-[#FF1493] bg-transparent'
    default:
      return 'bg-[#FF1493] text-white'
  }
})

const sizeClasses = computed(() => {
  switch (props.size) {
    case 'sm':
      return 'px-4 py-1.5 text-xs rounded-md'
    case 'lg':
      return 'px-10 py-4 text-base rounded-xl'
    case 'md':
    default:
      return 'px-6 py-2.5 text-sm rounded-lg'
  }
})
</script>