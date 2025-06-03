<template>
    <div id="title" class="text-white flex justify-center h-[80vh] items-center">
        <div class="mx-auto px-4 py-14 w-xs md:w-md text-center text-lg">
            <span class="text-2xl md:text-4xl font-semibold">{{ props.title }}</span><br><br>
            <span class="font-thin md:text-xl text-balance" v-html="props.content"></span>
        </div>
    </div>
</template>

<script setup>
const props = defineProps(['title', 'content'])
</script>

<style>
#title {
    font-family: 'Noto Serif TC', sans-serif;
}
</style>