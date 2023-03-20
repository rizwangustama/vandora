<script>
import anime from 'animejs/lib/anime.es.js'
import { ChevronDownIcon } from '@heroicons/vue/24/outline';
export default {
    components: {
        ChevronDownIcon
    },
    props: ['title', 'content'],
    methods: {
        getButtonFunction() {
            const getBottom = document.querySelector('.portopolio');
            getBottom.scrollIntoView({top: 0, behavior: 'smooth'});
        },
        animateText() {
            anime({
            targets: '.text',
            translateY: ['-50%', '0%'],
            opacity: [0, 1],
            easing: 'easeInOutQuad',
                duration: 1000,
                
            });
        },
    },

    mounted() {
        // anime({
        //     targets: '.effect-title',
        //     translateX: 250,
        //     duration: 1000,
        //     direction: 'alternate',
        //     loop: true,
        //     easing: 'easeInOutSine'
        // })
    },
}


</script>
<template>
    <section class="heros">
        <div class="container">
            <div class="h-screen flex items-center justify-center relative">
                <!-- <TheWelcome /> -->
                <!-- <h1>{{ props.data }}</h1> -->
                <button @click="getButtonFunction()" class="absolute left-1/2 -translate-x-1/2 bottom-10 border-2 border-slate-500 p-4 rounded-full">
                    <ChevronDownIcon class="w-6 h-6 text-slate-400"/>
                </button>
                <div class="flex flex-col items-center gap-4">
                    <h1 class="effect-title max-w-[800px] text-6xl font-bold text-center color-primary leading-tight">
                        {{ title }}</h1>
                    <p class="text-xl max-w-[780px] text-gray-400 text-center">{{ content }}</p>
                </div>
            </div>
        </div>
    </section>
</template>


<!-- 
<style scoped>
.heros{
    @apply relative;
}
</style> -->
