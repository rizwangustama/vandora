<script>
import {
    onMounted
} from 'vue';

import { MagnifyingGlassIcon, ArrowRightIcon } from '@heroicons/vue/24/outline';
import IconError from '../../components/icons/iconError.vue';
export default {
    components: {
        MagnifyingGlassIcon,
        ArrowRightIcon,
        IconError
    },
    data() {
        return {
            title: "ahdsahsj",
            content: "kjahjkdhajs",

            search: '',
            filterSelectCategory: '',

            dataFilter: [
                {
                    category: 'Web Develover',
                    slug: 'web-developer'
                },
                {
                    category: 'UI / UX Design',
                    slug: 'ui/ux-design'
                }
            ],
            data: [{
                    nama: 'Google 1',
                    slug: 'web-developer',
                    category: 'Web Develover',
                    image: 'https://images.unsplash.com/photo-1674919062539-c28df6cca151?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1770&q=80'
                },
                {
                    nama: 'Google 1',
                    slug: 'web-developer',
                    category: 'Web Develover',
                    image: 'https://images.unsplash.com/photo-1674919062539-c28df6cca151?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1770&q=80'
                },
                {
                    nama: 'Google 1',
                    slug: 'web-developer',
                    category: 'Web Develover',
                    image: 'https://images.unsplash.com/photo-1674919062539-c28df6cca151?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1770&q=80'
                },
                {
                    nama: 'Google 1',
                    slug: 'web-developer',
                    category: 'Web Develover',
                    image: 'https://images.unsplash.com/photo-1674919062539-c28df6cca151?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1770&q=80'
                },
                {
                    nama: 'Design',
                    slug: 'ui/ux-design',
                    category: 'UI / UX',
                    image: 'https://images.unsplash.com/photo-1674919062539-c28df6cca151?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1770&q=80'
                },
            ]
        }
    },
    computed: {
        filterCategory() {
            // if (this.filterSelectCategory !== '') {
            //     return this.data.filter(value => value.slug == this.filterSelectCategory);
            // } else if (this.search != '') {
            //     return this.data.filter(value => value.name.toLowerCase().includes(this.search.toLowerCase()))
            // }
            // else {
            //     return this.data;
            // }

            if (this.search !== '') {
                return this.data.filter(value => value.nama.toLowerCase().includes(this.search.toLowerCase()))
            } else if (this.filterSelectCategory !== '') {
                return this.data.filter(value => value.slug == this.filterSelectCategory);
            }
            else {
                return this.data;
            }

        }

    },
    methods: {
        // getDataFilter() {
        //     this.data.map((filter) => {
        //         return {
        //             category: filter.category,
        //             slug: filter.slug
        //         }
        //     })
        // }
    },
    mounted() {
        // this.dataFilter = this.data.map((filter) => {
        //     return {
        //         category: filter.category,
        //         slug: filter.slug
        //     }
        // });
    },
}
</script>
<template>
<div class="portopolio py-20">
    <div class="container">
        <div class="flex flex-col gap-1">
            <div class="flex flex-col mb-20">
                <h1 class="text-5xl font-bold text-center color-primary leading-normal">Projects Portfolio</h1>
                <p class="text-lg text-center text-slate-400 font-normal leading-normal">Search projects by title or filter by category</p>
            </div>

            <div class="flex justify-between">
                <div class="flex gap-4 w-1/3 pr-10">
                    <span class="p-3 bg-slate-800 rounded-lg">
                        <MagnifyingGlassIcon class="w-6 h-6"/>
                    </span>
                   
                    <input v-model="search" class="py-3 px-4 outline-sky-500 rounded-lg text-base bg-slate-800 text-slate-400 w-full" placeholder="Search" type="text">
                </div>
                
                <select class="py-3 px-4 bg-slate-800 rounded-lg text-base text-slate-400 outline-sky-500 w-1/6" v-model="filterSelectCategory">
                    <option value="" disabled="disable">Pilih Filter</option>
                    <template v-for="item in dataFilter">
                        <option :value="item.slug">{{item.category }}</option>
                    </template>
                </select>
            </div> 

            <div v-if="filterCategory.length != 0">
                <div class="grid grid-cols-3 gap-10 mt-10">
                    <template v-for="(item, index) in filterCategory" :key="index">
                        <div class="card bg-slate-800 rounded-xl overflow-hidden">
                            <div class="wrapper-image relative overflow-hidden">
                                <a href="#" class="absolute -bottom-20 z-10 bg-slate-600 py-6 w-full bg-opacity-80 rounded-tr-xl rounded-tl-xl flex justify-center">
                                
                                    <div class="flex items-center gap-4">
                                        <h4 class="text-lg text-center text-slate-300">Demo</h4>
                                        <span>
                                            <ArrowRightIcon class="w-4 h-4 text-slate-300"/>
                                        </span>
                                    </div>
                                
                                </a>
                                <img class="w-full object-cover" :src="item.image" :alt="item.nama">
                            </div>
                        
                            <div class="flex flex-col py-6 px-4">
                                <h1 class="font-semibold text-center text-lg color-primary leading-snug">{{ item.nama }}</h1>
                                <p class="text-base text-center font-normal leading-snug">{{ item.category }}</p>
                            </div>
                        
                        </div>
                    </template>

                </div>

                <div class="flex justify-center mt-20">
                    <a href="#" class="flex items-center justify-center gap-4 py-3 px-6 text-lg rounded-lg w-fit bg-secodary text-slate-800 font-semibold">
                        More Project
                        <ArrowRightIcon class="w-6 h-6 text-slate-800"/>
                    </a>
                </div>
            </div>

            <div v-else class="flex flex-col justify-center items-center py-10">

                <IconError/>
                <h3 class="text-xl">The data you are looking for does not exist</h3>
            </div>

        </div>
    </div>
</div>
</template>

<style scoped>

.wrapper-image a{
    transition: bottom .3s;
}
.wrapper-image:hover a{
    bottom: 0;
    transition: bottom .3s;
}
</style>
