<template>
  <header class="fixed top-0 left-0 right-0 z-50 ">
    <div class="max-w-7xl bg-white mx-auto px-6 py-4 flex items-center justify-between border-b border-[hotpink]">
      
      <nav class="flex gap-8 text-sm font-medium tracking-wide">
        <RouterLink
          v-for="item in navItems"
          :key="item.name"
          :to="item.path"
          class="group relative text-gray-500 transition-colors duration-200"
          active-class="text-pink-600"
        >
          {{ item.name }}

          <span
            class="pointer-events-none absolute left-1/2 -bottom-2 h-[2px] w-0
                   bg-pink-500 transition-all duration-300
                   group-hover:left-0 group-hover:w-full"
          ></span>
        </RouterLink>
      </nav>

      <RouterLink to="/login" class="flex gap-2">
        <BaseBtn size="sm" variant="primary">Login</BaseBtn>
      </RouterLink>

    </div>
  </header>
</template>

<script setup>
import BaseBtn from '../components/ui/BaseBtn.vue';

const navItems = [
  { name: 'Home', path: '/' },
  { name: 'About', path: '/about' },
]
</script>