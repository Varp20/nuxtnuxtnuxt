<template>
    <div class="flex gap-4">
        <label><input class ="mx-2" type = "radio" value ="cars" v-model = "selectedpic">Cars</label>
        <label><input class ="mx-2" type = "radio" value ="mac" v-model = "selectedpic">Mac</label>
        <label><input class ="mx-2" type = "radio" value ="kchau" v-model = "selectedpic">Kchau!</label>
    </div>
    <div class="flex flex-row gap-4 flex-wrap">
        <div class = "blockcap" v-if = "selectedpic == 'cars'">
            <img :src="pic1.image" class ="w-60 h-68 pt-2">
            <p class = "text-white text-x1">{{pic1.name}}</p>
        </div>

        <div class = "blockcap" v-if = "selectedpic == 'mac'   ">
            <img :src="pic2.image" class ="w-60 h-68 pt-2">
            <p class = "text-white text-x1">{{pic2.name}}</p>
        </div>

        <div class = "blockcap" v-if = "selectedpic == 'kchau' ">
            <img :src="pic3.image" class ="w-60 h-68 pt-2">
            <p class = "text-white text-x1">{{pic3.name}}</p>
        </div>

    </div>
    <div class="flex flex-row gap-4 flex-wrap">
        <div class="blockfor" v-for="(pic, index) in genpic" :key ="index">
            <img :src="pic.image" class = "w-60 h-68 pt-2">
            <p class ="text-white text-x1">{{pic.name}}</p>
        </div>
    </div>
</template>

<script setup lang ="ts">
import {reactive, ref} from 'vue'
interface stking {
    name: string,
    image: string
}

const pic1 = reactive<stking>({
    name: 'cars',
    image: '/mc.jpg'
})

const pic2 = reactive<stking>({
    name: 'mac',
    image: '/bs.jpg'
})

const pic3 = reactive<stking>({
    name: 'kchau',
    image: '/ma.jpg'
})

const genpic =reactive<stking[]>([
    {name: 'Bu', image: "/by.jpg"},
    {name: 'ZLodei Britanez', image: "/CC.jpg"},
    {name: 'Ama blue dabudi dabudai', image: "/CW.jpg"},
    {name: 'Kakoi-to muzhik', image: "/hs.jpg"},
    {name: 'Jackson Storm', image: "/js.jpg"},
    {name: 'Krutie Usbl bro', image: "/sf.jpg"},
    {name: 'It is 5 o clock my dudes', image: "/pz.jpg"},
])

const selectedpic = ref<string>('')
</script>

<style scoped>

    .blockap {
        @apply flex flex-col gap-2 border-purple-500 border bg-red-600 w-72 h-auto items-center hover:border-black hover:border-4 hover:bg-yellow-500;  
    }

    .blockfor {
       @apply flex flex-col gap-2 border-purple-500 border bg-red-600 w-72 h-auto items-center hover:border-green-950 hover:border-4 hover:bg-black;  
    }

</style>    