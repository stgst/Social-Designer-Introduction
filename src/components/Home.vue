ㄙㄣ
<script setup>
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
  <div class="text-white text-center flex flex-col items-center justify-center z-20  mb-[27vh]">
    <div class="flex justify-center gap-5">
      <a href="https://www.instagram.com/have_genderandluck/" target="_blank">
        <svg class="w-10 h-10 text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" width="24" height="24"
          fill="none" viewBox="0 0 24 24">
          <path fill="currentColor" fill-rule="evenodd"
            d="M3 8a5 5 0 0 1 5-5h8a5 5 0 0 1 5 5v8a5 5 0 0 1-5 5H8a5 5 0 0 1-5-5V8Zm5-3a3 3 0 0 0-3 3v8a3 3 0 0 0 3 3h8a3 3 0 0 0 3-3V8a3 3 0 0 0-3-3H8Zm7.597 2.214a1 1 0 0 1 1-1h.01a1 1 0 1 1 0 2h-.01a1 1 0 0 1-1-1ZM12 9a3 3 0 1 0 0 6 3 3 0 0 0 0-6Zm-5 3a5 5 0 1 1 10 0 5 5 0 0 1-10 0Z"
            clip-rule="evenodd" />
        </svg>
      </a>
      <a href="mailto:mail@xiung.me" target="_blank">
      <svg class="w-10 h-10 text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" width="24" height="24"
        fill="currentColor" viewBox="0 0 24 24">
        <path
          d="M17 6h-2V5h1a1 1 0 1 0 0-2h-2a1 1 0 0 0-1 1v2h-.541A5.965 5.965 0 0 1 14 10v4a1 1 0 1 1-2 0v-4c0-2.206-1.794-4-4-4-.075 0-.148.012-.22.028C7.686 6.022 7.596 6 7.5 6A4.505 4.505 0 0 0 3 10.5V16a1 1 0 0 0 1 1h7v3a1 1 0 0 0 1 1h2a1 1 0 0 0 1-1v-3h5a1 1 0 0 0 1-1v-6c0-2.206-1.794-4-4-4Zm-9 8.5H7a1 1 0 1 1 0-2h1a1 1 0 1 1 0 2Z" />
      </svg>
      </a>

    </div>
    <svg class="animate__animated animate__shakeY animate__infinite animate__slower mt-15 w-20 h-20" aria-hidden="true"
      xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24">
      <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
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