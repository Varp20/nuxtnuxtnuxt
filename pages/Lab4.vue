<template>
    <!-- Постоянные аудио -->
    <div class="flex flex-row gap-4 flex-wrap">
        <div class="blockfor" v-for="(aud, index) in genAudios" :key="index">
            <audio :src="aud.src" controls class="w-60 pt-2"></audio>
            <p class="text-white text-xl">{{ aud.name }}</p>
        </div>
    </div>

    <!-- Переключатель для аудио -->
    <div class="flex gap-4">
        <label><input class="mx-2" type="radio" value="audio1" v-model="selectedAudio"> Option 1</label>
        <label><input class="mx-2" type="radio" value="audio2" v-model="selectedAudio"> Option 2</label>
    </div>

    <!-- Выбранное аудио -->
    <div class="flex flex-row gap-4 flex-wrap">
        <div class="blockcap" v-if="selectedAudio === 'audio1'">
            <audio :src="audioOptions[0].src" controls class="w-60 pt-2"></audio>
            <p class="text-white text-xl">{{ audioOptions[0].name }}</p>
        </div>
        <div class="blockcap" v-if="selectedAudio === 'audio2'">
            <audio :src="audioOptions[1].src" controls class="w-60 pt-2"></audio>
            <p class="text-white text-xl">{{ audioOptions[1].name }}</p>
        </div>
    </div>

    <!-- Постоянные видео -->
    <div class="flex flex-row gap-4 flex-wrap">
        <div class="blockfor" v-for="(vid, index) in genVideos" :key="index">
            <video :src="vid.src" controls class="w-60 h-40 pt-2"></video>
            <p class="text-white text-xl">{{ vid.name }}</p>
        </div>
    </div>

    <!-- Переключатель для видео -->
    <div class="flex gap-4">
        <label><input class="mx-2" type="radio" value="video1" v-model="selectedVideo"> Option 1</label>
        <label><input class="mx-2" type="radio" value="video2" v-model="selectedVideo"> Option 2</label>
    </div>

    <!-- Выбранное видео -->
    <div class="flex flex-row gap-4 flex-wrap">
        <div class="blockcap" v-if="selectedVideo === 'video1'">
            <video :src="videoOptions[0].src" controls class="w-60 h-40 pt-2"></video>
            <p class="text-white text-xl">{{ videoOptions[0].name }}</p>
        </div>
        <div class="blockcap" v-if="selectedVideo === 'video2'">
            <video :src="videoOptions[1].src" controls class="w-60 h-40 pt-2"></video>
            <p class="text-white text-xl">{{ videoOptions[1].name }}</p>
        </div>
    </div>
</template>

<script setup lang="ts">
import { reactive, ref } from 'vue'

interface MediaItem {
    name: string,
    src: string
}

// Постоянные аудио
const genAudios = reactive<MediaItem[]>([
    { name: 'Cool Song', src: '/cool.mp3' },
    { name: 'Relax Tune', src: '/relax.mp3' }
])

// Аудио на выбор
const audioOptions = reactive<MediaItem[]>([
    { name: 'Option 1 Audio', src: '/audio1.mp3' },
    { name: 'Option 2 Audio', src: '/audio2.mp3' }
])

// Постоянные видео
const genVideos = reactive<MediaItem[]>([
    { name: 'Epic Clip', src: '/epic.mp4' },
    { name: 'Funny Clip', src: '/funny.mp4' }
])

// Видео на выбор
const videoOptions = reactive<MediaItem[]>([
    { name: 'Option 1 Video', src: '/video1.mp4' },
    { name: 'Option 2 Video', src: '/video2.mp4' }
])

const selectedAudio = ref<string>('audio1')
const selectedVideo = ref<string>('video1')
</script>

<style scoped>
.blockcap {
    @apply flex flex-col gap-2 border-purple-500 border bg-red-600 w-72 h-auto items-center hover:border-black hover:border-4 hover:bg-yellow-500;  
}

.blockfor {
    @apply flex flex-col gap-2 border-purple-500 border bg-red-600 w-72 h-auto items-center hover:border-green-950 hover:border-4 hover:bg-black;  
}
</style>
