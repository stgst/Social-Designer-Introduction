<template>
    <div id="title" class="relative z-10 text-white flex justify-center items-center">
        <div class="mx-auto px-4 py-14 w-xs md:w-md text-center text-lg">
            <br><br>
            <span class="text-2xl font-semibold">讓你的故事被看見</span><br><br>
            <form @submit.prevent="submitFunc">
                <div class="w-full mb-4 border border-gray-200 rounded-xl bg-white/80">
                    <div class="px-4 py-2 bg-transparent rounded-t-lg">
                        <label for="comment" class="sr-only">寫下你的故事</label>
                        <textarea id="comment" name="comment" v-model="comment" rows="10"
                            class="w-full px-0 text-sm text-gray-900 bg-transparent border-0 focus:ring-0 focus:outline-none"
                            placeholder="寫下你的故事" required></textarea>
                    </div>
                    <div class="flex items-center justify-center px-3 py-2">
                        <button id="submitBtn" type="submit" :disabled="!isAgreed" :class="[
                            'inline-flex items-center py-2.5 px-20 text-xs font-semibold rounded-lg shadow-lg transition-all duration-300',
                            isAgreed ? 'bg-white text-black hover:bg-gray-100 hover:cursor-pointer' : 'bg-gray-300 text-gray-500 cursor-not-allowed'
                        ]">
                            送出
                        </button>
                    </div>
                </div>
            </form>
            <div class="flex items-center justify-center">
                <input id="link-radio" type="checkbox" v-model="isAgreed" value="agreed"
                    class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 focus:ring-blue-500">
                <label for="link-radio" class="ms-2 text-sm font-medium text-white">
                    勾選並同意<button @click="handleShowModal" class="text-blue-400 hover:cursor-pointer ">隱私權保護聲明</button>
                </label>
            </div>
            <br><br>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue'

var isAgreed = defineModel('isAgreed', {
    type: Boolean,
    default: false
})

const emit = defineEmits(['openModal'])

const handleShowModal = () => {
    emit('openModal')
}

const comment = ref('')

const submitFunc = () => {
    var submitBtn = document.getElementById('submitBtn')
    submitBtn.textContent = '提交中...'
    isAgreed.value = false

    var url = "https://script.google.com/macros/s/AKfycbzIqLQyr_xsshA-idgUDZAHVDq6FpKbiSQTXV2ckTuXuL7Zf2H02EnTyAvYu-O8eSp3/exec"
    fetch(url, {
        method: 'POST',
        headers: {
            'Content-Type': 'application/x-www-form-urlencoded'
        },
        body: new URLSearchParams({
            'comment': comment.value
        })
    }).then(response => {
        if (response.value = "Comment saved successfully") {
            alert('提交成功，感謝您的分享！')
            submitBtn.textContent = '送出'
            comment.value = '' // 清空輸入框
        } else {
            alert('提交失敗，請稍後再試。')
        }
    }).catch(error => {
        console.error('Error:', error)
        alert('提交失敗，請稍後再試。')
    })
}

</script>

<style>
#title {
    font-family: 'Noto Serif TC', sans-serif;
}
</style>
