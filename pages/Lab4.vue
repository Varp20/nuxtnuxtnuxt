<template>

    <div class="flex flex-row gap-4 flex-wrap">
        <div class="blockfor" v-for="(aud, index) in genAudios" :key="index">
            <audio :src="aud.src" controls class="w-60 pt-2"></audio>
            <p class="text-white text-xl">{{ aud.name }}</p>
        </div>
    </div>

    <div class="flex gap-4">
        <label><input class="mx-2" type="radio" value="audio1" v-model="selectedAudio"> Option 1</label>
        <label><input class="mx-2" type="radio" value="audio2" v-model="selectedAudio"> Option 2</label>
    </div>

    <div class="flex flex-row gap-4 flex-wrap mb-5  ">
        <div class="blockcap" v-if="selectedAudio === 'audio1'">
            <audio :src="audioOptions[0].src" controls class="w-60 pt-2"></audio>
            <p class="text-white text-xl">{{ audioOptions[0].name }}</p>
        </div>
        <div class="blockcap" v-if="selectedAudio === 'audio2'">
            <audio :src="audioOptions[1].src" controls class="w-60 pt-2"></audio>
            <p class="text-white text-xl">{{ audioOptions[1].name }}</p>
        </div>
    </div>

    <div class="flex flex-row gap-4 flex-wrap px-8 mb-5">
        <div class="blockfor" v-for="(vid, index) in genVideos" :key="index">
            <video :src="vid.src" controls class="w-60 h-40 pt-2"></video>
            <p class="text-white text-xl">{{ vid.name }}</p>
        </div>
    </div>

    <div class="flex gap-4">
        <label><input class="mx-2" type="radio" value="video1" v-model="selectedVideo"> Option 1</label>
        <label><input class="mx-2" type="radio" value="video2" v-model="selectedVideo"> Option 2</label>
    </div>

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

const genAudios = reactive<MediaItem[]>([
    { name: 'Puziriki', src: '/1.mp3' },
    { name: 'Relax Tune', src: '/2.mp3' }
])

const audioOptions = reactive<MediaItem[]>([
    { name: 'Me when always:', src: '/3.mp3' },
    { name: 'Zachem ti igraesh na moih barabanah', src: '/4.mp3' }
])

const genVideos = reactive<MediaItem[]>([
    { name: 'No no no mister Fish', src: '/1.mp4' },
    { name: 'Zdes videosiemka zapreshena', src: '/2.mp4' }
])

const videoOptions = reactive<MediaItem[]>([
    { name: 'Funny dog', src: '/3.mp4' },
    { name: 'CARROOOOOOT!!!', src: '/4.mp4' }
])

const selectedAudio = ref<string>('audio1')
const selectedVideo = ref<string>('video1')
</script>

<style scoped>
.blockcap {
    @apply flex flex-col gap-2 border-purple-500  bg-red-600 w-72 h-auto items-center hover:border-black hover:border-4 hover:bg-yellow-500;  
}

.blockfor {
    @apply flex flex-col gap-2 border-purple-500  bg-red-600 w-72 h-auto items-center hover:border-green-950 hover:border-4 hover:bg-black;  
}
</style>
