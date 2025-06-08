<script setup>
import { ref, reactive } from 'vue'
import { useHead } from '@vueuse/head'
import Home from '@/components/Home.vue'
import Intro from '@/components/Intro.vue'
import Forms from '@/components/Form.vue'
import Notice from '@/components/Notice.vue'
import ogImage from '@/assets/img/og-image.jpg'  // 新增這行

const baseurl = "https://havegenderluck.org"
useHead({
  title: '〈留下來的不止影像〉',
  meta: [
    { name: 'viewport', content: 'width=device-width, initial-scale=1' },
    { property: 'og:title', content: '〈留下來的不止影像〉' },
    { property: 'og:description', content: '一個關於數位性別暴力的倡議行動，讓每一段經歷都值得被看見。' },
    { property: 'og:image', content: `${baseurl}${ogImage}` },  // 修改這行
    { property: 'og:url', content: 'https://havegenderluck.org/' },
    { name: 'description', content: '一個關於數位性別暴力的倡議行動，讓每一段經歷都值得被看見。' },
    { name: 'keywords', content: '數位性別暴力, 數位性暴力, 社會設計, 社會設計師, 數位正義' },
    { name: 'author', content: 'Social Designer' }
  ]
})

const isModalVisible = ref(false)
const introSections = reactive([
  {
    title: '《那張照片不是我給的》',
    content: '高二那年，我和他在一起不到三個月。說不清是喜歡還是想被喜歡，但我信任他，拍了一張只有他會看到的照片。沒想到幾週後，我發現班上幾個男生對我竊竊私語，甚至還有人在 IG 上匿名傳我照片的截圖。那一刻我好像被人從身體裡撕開，我不知道怎麼證明那是「被外流」、不知道能告誰、也不敢說出口。<br><br>他後來說：<br>「又不是我傳的，我只是讓我朋友看一下。」<br><br>但就是那個「看一下」，讓我變得無所遁形。我不是唯一的受害者，但我希望我是最後一個。'
  },
  {
    title: '我們想聽見你的聲音',
    content: '在面對數位性暴力的經驗中，很多人選擇沉默，不是因為不痛，而是因為不知道可以說給誰聽。這裡是一個安全的空間，我們相信——每一段經歷都值得被理解、被記錄、被看見。<br><br>你可以選擇匿名、隱去細節，我們會小心保護每個字句。你的故事，不只是你的傷口，更是未來改變的開始。'
  },
  {
    title: '有「性」可談',
    content: '我們是由 3 位大學生與 1 位高中生組成的 Social Designer 參賽團隊，關注數位性別暴力與其背後的結構性不平等。我們看見在看似輕微的點擊、轉傳與沉默背後，潛藏著對受害者長遠且深刻的傷害。本專案〈留下來的不止影像〉，旨在透過互動體驗與情境設計，引導大眾深入瞭解數位性別暴力，透過倡議行動增加人們對「轉傳」與「旁觀」等行為的重視，喚起更多人對數位性別正義的關注與行動。'
  }
])
const teamTitle = { title: '團隊成員', content: '<p class="text-2xl font-medium">東吳大學政治系</p>王宣雅<br>陳咨貝<br>林　潔<br><br><p class="text-2xl font-medium">臺北市數位實驗高中</p>詹啟翔' }

const showModal = () => {
  isModalVisible.value = true
}

const closeModal = () => {
  isModalVisible.value = false
}
</script>

<template>
  <div id="bg" class="fixed inset-0 -z-10 bg-cover bg-center"></div>
  <div id="bg-wrapper" class="fixed inset-0 -z-10 bg-black opacity-50"></div>

  <div class="relative min-h-screen z-10">
    <Home />
    <Intro v-for="(section, index) in introSections" :key="index" :title="section.title" :content="section.content" />
    <div class="relative z-20 flex items-center justify-center h-screen">
      <Forms class="relative z-10" @openModal="showModal" />
      <Notice class="absolute" v-show="isModalVisible" :isModalVisible="isModalVisible" @close="closeModal" />
    </div>
    <Intro :title="teamTitle.title" :content="teamTitle.content" />
  </div>
</template>

<style>
#bg {
  background-image: url('@/assets/img/bg.jpg');
}
</style>
