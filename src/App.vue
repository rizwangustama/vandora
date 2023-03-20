<script>
import {
    useDark,
    useToggle
} from '@vueuse/core';
import {
  RouterLink,
  RouterView
} from 'vue-router';

import { reactive, ref } from 'vue';

import { MoonIcon, SunIcon, ChevronUpIcon } from '@heroicons/vue/24/outline';

export default {
  components: {
    MoonIcon,
    SunIcon,
    ChevronUpIcon
  },
  data() {
    return {
      showScrollTopBtn: false,
    }
  },
  setup(props) {
    const isDark = useDark();
    const toggleDark = useToggle(isDark);
    // const showScrollTopBtn = reactive(false);

    return {
      isDark,
      toggleDark,
      // showScrollTopBtn
    }
  },

  methods: {
    getTop() {
      window.scrollTo({ top: 0, behavior: 'smooth'})
    },

    scrollFunction() {
      if (window.pageYOffset > 20) {
        this.showScrollTopBtn = true;
      } else {
        this.showScrollTopBtn = false;
      }
    }
  },

  mounted() {
    // console.log(window.pageYOffset);
    window.addEventListener('scroll', this.scrollFunction);
  },

  beforeDestroy() {
    window.removeEventListener('scroll', this.scrollFunction);
  },
 
}

</script>

<template>
<header :class="{ absolute: $route.name == 'home' }" class="w-full z-10">
    <div class="container flex items-center justify-between py-3">
      <h2 class="color-primary dark:text-white text-gray-800 text-2xl font-semibold">Vandora Developer</h2>
        <div class="wrapper flex items-center">
            <nav class="flex">
                <RouterLink class="text-lg font-normal dark:text-white text-emerald-500" to="/">Project</RouterLink>
                <RouterLink class="text-lg font-normal dark:text-white text-emerald-500" to="/about">About Me</RouterLink>
                <RouterLink class="text-lg font-normal dark:text-white text-emerald-500" to="/about">Contact</RouterLink>
                <RouterLink class="text-lg font-normal dark:text-white text-emerald-500" to="/blog">Blog</RouterLink>
            </nav>
           
        </div>

        <div class="flex gap-6">
          <button class="text-base text-gray-800 px-6 rounded-lg font-medium bg-secodary">Download CV</button>
          <button @click="toggleDark()" class="dark:text-gray-700 rounded-lg text-white p-3 dark:bg-gray-700 bg-emerald-500">
            <MoonIcon v-if="isDark" class="h-6 w-6 text-white"/>
            <SunIcon v-else class="h-6 w-6"/>
          </button>
          
        </div>
    </div>
</header>

<RouterView/>

<button v-if="showScrollTopBtn" @click="getTop()" class="sticky bottom-[48px] left-[93%] p-4 rounded-full bg-slate-800">
  <ChevronUpIcon class="w-6 h-6 text-white"/>
</button>

</template>

<style scoped>
header nav a {
    @apply py-2 px-4;
}
</style>
