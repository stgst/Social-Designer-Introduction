<template>
    <div id="title" class="text-white flex justify-center items-center animate__animated animate__fadeIn">
        <div class="mx-auto px-4 w-xs md:w-md text-center text-lg">
            <br><br>
            <div class="bg-white shadow-lg rounded-xl p-10 text-black text-left">
                <div class="flex justify-between mb-6">
                    <h1 class="text-2xl font-bold text-center">注意事項</h1>
                    <button @click="$emit('close')" class="hover:cursor-pointer">
                        <svg class="w-6 h-6 text-gray-800 dark:text-white " aria-hidden="true"
                            xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24">
                            <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                d="M6 18 17.94 6M18 18 6.06 6" />
                        </svg>
                    </button>
                </div>
                <p class="mb-4">
                    所有提交的故事與資料，將嚴格遵守《個人資料保護法》及其他相關法律規範。我們僅蒐集您自願提供的資訊，並確保其用途僅限於研究、分析與推廣數位性暴力防治之目的，絕不挪作他用。您的個人身分資訊（如姓名、聯繫方式或其他可辨識資料）將受到嚴密保護，未經您的明確同意，絕不會公開或分享予第三方。若您選擇匿名分享，我們將確保您的故事以完全去識別化的方式呈現於我們的社群平台，保護您的隱私不受侵害。
                </p>
            </div>
            <br><br>
        </div>
    </div>
</template>

<script setup>
</script>

<style>
#title {
    font-family: 'Noto Serif TC', sans-serif;
}

.animate__animated {
    animation-duration: 0.5s;
}
</style>