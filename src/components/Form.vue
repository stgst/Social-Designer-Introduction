<template>
    <div id="title" class="text-white flex justify-center h-screen items-center">
        <div class="mx-auto px-4 py-14 w-xs md:w-md text-center text-lg">
            <br><br>
            <span class="text-2xl font-semibold">讓你的故事被看見</span><br><br>
            <form>
                <div class="w-full mb-4 border border-gray-200 rounded-xl bg-white/80">
                    <div class="px-4 py-2 bg-transparent rounded-t-lg">
                        <label for="comment" class="sr-only">寫下你的故事</label>
                        <textarea 
                            id="comment" 
                            rows="10" 
                            class="w-full px-0 text-sm text-gray-900 bg-transparent border-0 focus:ring-0 focus:outline-none" 
                            placeholder="寫下你的故事" 
                            required
                        ></textarea>
                    </div>
                    <div class="flex items-center justify-center px-3 py-2">
                        <button type="submit" 
                                :disabled="!isAgreed"
                                :class="[
                                    'inline-flex items-center py-2.5 px-20 text-xs font-semibold rounded-lg shadow-lg transition-all duration-300',
                                    isAgreed ? 'bg-white text-black hover:bg-gray-100 hover:cursor-pointer' : 'bg-gray-300 text-gray-500 cursor-not-allowed'
                                ]">
                            送出
                        </button>
                    </div>
                </div>
            </form>
            <div class="flex items-center justify-center">
                <input id="link-radio" 
                       type="checkbox" 
                       v-model="isAgreed"
                       value="agreed"
                       class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 focus:ring-blue-500">
                <label for="link-radio" class="ms-2 text-sm font-medium text-white">
                    勾選並同意<a href="#" class="text-blue-400 hover:underline">使用條款</a>
                </label>
            </div>
            <br><br>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue'

const isAgreed = ref('')

const handleRadioChange = () => {
    // radio button 不需要額外的 change handler
    // v-model 會自動處理狀態
}
</script>

<style>
#title {
    font-family: 'Noto Serif TC', sans-serif;
}
</style>