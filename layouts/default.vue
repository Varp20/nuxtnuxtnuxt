<template>
    <header class="flex flex-row w-full items-center relative  bg-cyan-700 border-b2 border-gray-400 max-sm: justify-between max-sm:relative">
        <div class = "basis-1/4 items-center justify-start px-8 min-w-40 max-sm:basis-auto">
            <img src="assets/images/hk416.gif" class="w-16 h-16">
        </div>
        <div class="basis-1/4 max-sm:basis-auto">
        </div>
        <nav :class= "{'basis-1/2 flex flex-row items-center justify-end px-8 gap-4' : !burger || burger,
        'max-sm:basis-auto max-sm:absolute max-sm:top-full max-sm:w-full max-sm:justify-center max-sm:flex-col max-sm:gap-0 max-sm:bg-rose-400 max-sm:px-0': burger,
        'max-sm:hidden': !burger}">
            <NuxtLink to = "/" class = "my-auto p-2 hover:bg-red-700 hover:text-purple-950 max-sm:w-full max-sm:border-b-2 max-sm:text-center">Home</NuxtLink>
        <div class= "my-auto p-2 hover:bg-red-700 hover:text-purple-950 max-sm:w-full max-sm:border-b-2 max-sm:text-center max-sm:px-0 max-sm:pb-0" @click = "switch_submenu">Labs
          <div class="flex flex-col absolute top-full bg-red-800 text-black w-56 text-center max-sm:relative max-sm:w-full max-sm:bg-red-800" v-show="submenu">
            <NuxtLink to = "/Lab3" class="my-auto p-2 border-b-2 hover:bg-red-700 hover:text-purple-950 max-sm:w-full max-sm:border-t-2 max-sm:text-center">Lab3</NuxtLink>
            <NuxtLink to = "/Lab4" class="my-auto p-2 border-b-2 hover:bg-red-700 hover:text-purple-950 max-sm:w-full max-sm:text-center">Lab4</NuxtLink>
            <NuxtLink to = "/Lab5" class="my-auto p-2 border-b-2 hover:bg-red-700 hover:text-purple-950 max-sm:w-full max-sm:text-center">Lab5</NuxtLink>
            <NuxtLink to = "/Lab6" class="my-auto p-2 border-b-2 hover:bg-red-700 hover:text-purple-950 max-sm:w-full max-sm:border-black max-sm:text-center">Lab6</NuxtLink>
          </div>
        </div>
        <NuxtLink to ="/login" :class="{'my-auto p-2 hover:bg-red-700 hover:text-purple-950 max-sm:w-full max-sm:border-b-2 max-sm:text-center':submenu,
        'my-auto p-2 hover:bg-red-700 hover:text-purple-950 max-sm:w-full max-sm:border-t-2 max-sm:text-center': !submenu}">LogIn</NuxtLink>
        <NuxtLink to ="/logout" class="my-auto p-2 hover:bg-red-700 hover:text-purple-950 max-sm:w-full max-sm:border-b-2 max-sm:text-center">LogOut</NuxtLink>    
    </nav>
    <div v-if = "!burger" @click = "switch_burger" class = "max-sm:flex max-sm:flex-col max-sm:mr-8 max-sm:justify-between max-sm:items-center max-sm:w-8 max-sm:h-6">
        <span class = "h-[3px] w-full bg-yellow-200"></span>
        <span class = "h-[3px] w-full bg-yellow-200"></span>
        <span class = "h-[3px] w-full bg-yellow-200"></span>
    </div>
    <div v-else class = "max-sm:flex max-sm:flex-col max-sm:mr-8 max-sm:justify-between max-sm:items-center max-sm:w-8 max-sm:h-6" @click = "switch_burger">
        <span class = "h-[3px] w-full bg-yellow-200 rotate-45 relative top-[9px]"></span>
        <span class = "h-[3px] w-full bg-yellow-200 opacity-0"></span>
        <span class = "h-[3px] w-full bg-yellow-200 relative bottom-3 rotate-[-45deg]"></span>
    </div>
    </header>

    <main class ="p-5 flex flex-col items-center justify-center min-h-screen flex-wrap bg-yellow-500 ">
        <slot />
    </main>

    <footer class="flex flex-row mt-auto w-full bg-yellow-200 border-t-2 border-green-700 items-center justify-center px-4 py-2 gap-4">
        <a href="https://www.youtube.com/watch?v=dQw4w9WgXcQ"><img src="assets/images/youtube.png" class="w-16 h-16"></a>
        <a href="https://steamcommunity.com/profiles/76561198088932851"><img src="assets/images/steam.jpg" class="w-16 h-16"></a>
        <a href="https://ru.wikipedia.org/wiki/%D0%A0%D0%B8%D0%BA%D1%80%D0%BE%D0%BB%D0%BB%D0%B8%D0%BD%D0%B3"><img src="assets/images/wiki.png" class="w-16 h-16 bg-transparent"></a>
    </footer>
</template>

<script setup lang = 'ts'>
import {useHead} from '#app';
import {ref} from 'vue'

useHead({   
    script: [
        {
            async:true,
            src: 'https://www.googletagmanager.com/gtag/js?id=G-DQ0X2JFFN2',
        },
        {
            innerHTML: `
            window.dataLayer = window.dataLayer || [];
            function gtag(){dataLayer.push(arguments);}
            gtag('js',new Date());
            gtag('config', 'G-DQ0X2JFFN2');
            `,
            type: 'text/javascript',
        },
    ],
    __dangerouslyDisableSanitizersByTagID: {
        gtag: ['innerHTML'],
    },
});

const burger = ref <boolean> (false)
const submenu = ref <boolean> (false)


const switch_burger = ()=> {burger.value = !burger.value}
const switch_submenu = ()=> {submenu.value = !submenu.value}

</script>