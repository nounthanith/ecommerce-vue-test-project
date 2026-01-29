<template>
  <section
    class="relative w-full max-w-7xl mx-auto overflow-hidden
           min-h-[220px] sm:min-h-[320px] md:min-h-[420px] lg:min-h-[520px]"
  >

    <!-- Progress bar -->
    <div
      class="absolute top-0 left-0 z-0 h-1 bg-[#FF1493] transition-all duration-300"
      :style="{ width: `${((activeIndex + 1) / features.length) * 100}%` }"
    ></div>

    <!-- Slider -->
    <div
      ref="slider"
      class="flex w-full h-full overflow-x-auto snap-x snap-mandatory scroll-smooth no-scrollbar"
      @scroll="handleScroll"
    >
      <div
        v-for="(feature, index) in features"
        :key="index"
        class="relative shrink-0 snap-center w-full aspect-video sm:aspect-21/9"
      >
        <img
          :src="feature.image"
          class="w-full h-full object-cover transition-transform duration-2000"
          :class="{ 'scale-105': activeIndex === index }"
          alt="Feature"
        />
      </div>
    </div>

    <!-- Dots (hidden on mobile) -->
    <div
      class="absolute right-4 top-1/2 -translate-y-1/2 z-40
             hidden sm:flex flex-col gap-3"
    >
      <button
        v-for="(_, i) in features"
        :key="i"
        @click="scrollTo(i)"
        class="group flex items-center justify-end"
      >
        <span
          class="mr-2 opacity-0 group-hover:opacity-100
                 text-white text-xs font-bold tracking-widest"
        >
          0{{ i + 1 }}
        </span>
        <div
          class="h-1 rounded-full transition-all duration-500"
          :class="activeIndex === i
            ? 'w-8 bg-[#FF1493]'
            : 'w-4 bg-white/40 hover:bg-white'"
        ></div>
      </button>
    </div>

    <!-- Counter -->
    <div class="absolute bottom-4 left-4 z-40 flex items-baseline gap-2 text-white">
      <span class="text-lg sm:text-xl md:text-2xl font-light">
        0{{ activeIndex + 1 }}
      </span>
      <span class="text-white/40">/</span>
      <span class="text-white/40 text-xs sm:text-sm">
        0{{ features.length }}
      </span>
    </div>

  </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import featureData from '../utils/featureData'

const features = ref(featureData)
const slider = ref(null)
const activeIndex = ref(0)
const containerWidth = ref(0)
let autoScrollTimer = null

const updateWidth = () => {
  if (slider.value) containerWidth.value = slider.value.offsetWidth
}

const handleScroll = (event) => {
  if (!containerWidth.value) return
  activeIndex.value = Math.round(event.target.scrollLeft / containerWidth.value)
}

const scrollTo = (index) => {
  if (!slider.value) return
  slider.value.scrollTo({
    left: containerWidth.value * index,
    behavior: 'smooth'
  })
  activeIndex.value = index
}

const startAutoScroll = () => {
  autoScrollTimer = setInterval(() => {
    const nextIndex = (activeIndex.value + 1) % features.value.length
    scrollTo(nextIndex)
  }, 8000)
}

const stopAutoScroll = () => {
  if (autoScrollTimer) clearInterval(autoScrollTimer)
}

onMounted(() => {
  updateWidth()
  window.addEventListener('resize', updateWidth)
  startAutoScroll()
})
onUnmounted(() => {
  window.removeEventListener('resize', updateWidth)
  stopAutoScroll()
})
</script>

<style scoped>
/* Hide scrollbar */
.no-scrollbar::-webkit-scrollbar { display: none; }
.no-scrollbar { -ms-overflow-style: none; scrollbar-width: none; }

/* Smooth zoom for active image */
img { will-change: transform; }
</style>