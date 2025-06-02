ㄙㄣ<script setup>
import { ref, onMounted } from 'vue'

const showBg = ref(false)
const titleRef = ref(null)
const triggerRef = ref(null)

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      showBg.value = !entry.isIntersecting
    })
  }, {
    rootMargin: '-100px 0px 0px 0px', // 調整觸發點
    threshold: 0
  })

  if (triggerRef.value) {
    observer.observe(triggerRef.value)
  }
})
</script>

<template>
    <!-- 觸發點 -->
    <div ref="triggerRef" class="h-1 w-full absolute top-0"></div>
    
    <div ref="titleRef" id="title" class="sticky top-0 mt-[35vh]">
        <div class="flex items-center justify-center transition-all duration-300" 
             :class="{ 'bg__title bg-black/50 backdrop-blur-sm shadow-lg': showBg }">
            <div class="text-center text-white py-6">
                <h1 class="text-4xl">〈留下來的不止影像〉</h1>
                <p class="text-2xl opacity-70">有「性」可談</p>
            </div>
        </div>
    </div>
    <div class="text-white text-center flex flex-col items-center justify-center z-20 mt-15 mb-[27vh]">
        <svg class="animate__animated animate__shakeY animate__infinite animate__slower w-20 h-20" 
             aria-hidden="true"
             xmlns="http://www.w3.org/2000/svg" 
             width="24" 
             height="24" 
             fill="none" 
             viewBox="0 0 24 24">
            <path stroke="currentColor" 
                  stroke-linecap="round" 
                  stroke-linejoin="round" 
                  stroke-width="2"
                  d="M12 19V5m0 14-4-4m4 4 4-4" />
        </svg>
    </div>
</template>

<style>
#title {
    font-family: 'Noto Serif TC', sans-serif;
    font-weight: 600;
    z-index: 50;
}

.bg__title {
    transition: all 0.3s ease;
}
</style>