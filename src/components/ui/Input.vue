<template>
  <div class="w-full space-y-1.5">
    <label 
      v-if="label" 
      :for="id" 
      class="block text-xs font-semibold uppercase tracking-wider text-gray-500 ml-1"
    >
      {{ label }}
    </label>

    <div class="relative group">
      <input
        :id="id"
        :type="type"
        :value="modelValue"
        :placeholder="placeholder"
        :disabled="disabled"
        @input="$emit('update:modelValue', $event.target.value)"
        class="w-full bg-white transition-all duration-300 outline-none border border-gray-200 focus:border-[#FF1493] focus:ring-4 focus:ring-pink-500/10"
        :class="[sizeClasses, error ? 'border-red-500' : '']"
      />

      <div class="absolute bottom-0 left-1/2 h-[2px] w-0 -translate-x-1/2 bg-[#FF1493] transition-all duration-300 group-focus-within:w-full"></div>
    </div>

    <p v-if="error" class="text-[11px] text-red-500 mt-1 ml-1 font-medium">
      {{ error }}
    </p>
  </div>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  modelValue: [String, Number],
  label: String,
  placeholder: String,
  id: String,
  type: {
    type: String,
    default: 'text'
  },
  size: {
    type: String,
    default: 'md' // sm | md | lg
  },
  error: String,
  disabled: Boolean
})

defineEmits(['update:modelValue'])

const sizeClasses = computed(() => {
  switch (props.size) {
    case 'sm':
      return 'px-3 py-1.5 text-xs rounded-md'
    case 'lg':
      return 'px-5 py-3.5 text-base rounded-xl'
    case 'md':
    default:
      return 'px-4 py-2.5 text-sm rounded-lg'
  }
})
</script>