<template>
  <div class="flex flex-col">
    <div class="relative aspect-square overflow-hidden rounded-none bg-gray-50 border border-gray-100 flex items-center justify-center">
      
      <span class="relative flex h-10 w-10">
        <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-[#FF1493] opacity-20"></span>
        <span class="relative inline-flex rounded-full h-10 w-10 bg-[#FF1493]/10 border border-[#FF1493]/20"></span>
      </span>

      <div class="absolute inset-0 -translate-x-full bg-linear-to-r from-transparent via-white/60 to-transparent animate-shimmer"></div>
    </div>

    <div class="mt-4 flex flex-col items-center space-y-2">
      <div class="h-2 w-16 bg-pink-50 rounded-full"></div> <div class="h-3 w-32 bg-gray-100 rounded-full"></div> <div class="h-3 w-12 bg-gray-50 rounded-full"></div> </div>
  </div>
</template>

<style scoped>
@keyframes shimmer {
  0% { transform: translateX(-100%); }
  100% { transform: translateX(100%); }
}
.animate-shimmer { animation: shimmer 2s infinite; }
</style>