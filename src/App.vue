<script setup>
import { ref, computed, provide } from 'vue'
import Home from '@/components/Home.vue'
import Intro from '@/components/Intro.vue'
</script>

<template>
  <div id="bg" class="fixed inset-0 -z-10 bg-cover bg-center"></div>
  <div id="bg-wrapper" class="fixed inset-0 -z-10 bg-black opacity-50"></div>

  <div class="w-full max-w-4xl flex flex-col items-center justify-center mx-auto relative min-h-screen z-10">
    <Home />
    <Intro />
  </div>

</template>

<style>
#bg {
  background-image: url('@/assets/img/bg.jpg');
  /* 用 @ 指定 Vite 的靜態路徑 */
}
</style>
