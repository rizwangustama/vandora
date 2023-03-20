<template>
    <section class="contact-us">
        <div class="container h-screen flex items-center justify-center">
            <div>

            <div class="flex gap-6 flex-col justify-center items-center">
                <h3 class="max-w-[700px] text-center text-6xl color-primary font-bold">{{ data.title }}</h3>
                <p class="text-xl max-w-[600px] text-center">{{ data.content }}</p>
            </div>

            <div class="flex gap-10 justify-center mt-10">

           
                <a class="p-4 border border-slate-600 hover:bg-slate-800 transition-all rounded-full" href="#">
                    <linkedin :styleClass="'w-6 h-6'"/>
                </a>
                <a class="p-4 border border-slate-600 hover:bg-slate-800 transition-all rounded-full" href="#">
                    <github :styleClass="'w-6 h-6'"/>
                </a>
                <a class="p-4 border border-slate-600 hover:bg-slate-800 transition-all rounded-full" href="#">
                    <facebook :styleClass="'w-6 h-6'"/>
                </a>
                <a class="p-4 border border-slate-600 hover:bg-slate-800 transition-all rounded-full" href="#">
                    <twitter :styleClass="'w-6 h-6'"/>
                </a>
                <a class="p-4 border border-slate-600 hover:bg-slate-800 transition-all rounded-full" href="#">
                    <instagram :styleClass="'w-6 h-6'"/>
                </a>
            </div>
        </div>
        </div>  
    </section>
</template>
<script>

import linkedin from '../../components/icons/linkedin.vue';
import github from '../../components/icons/IconGithub.vue';
import facebook from '../../components/icons/IconFacebook.vue';
import twitter from '../../components/icons/IconTwitter.vue';
import instagram from '../../components/icons/IconInstagram.vue';

export default {
    components: {
        linkedin,
        github,
        facebook,
        twitter,
        instagram
    },
    data() {
        return {
            data: {
                title: 'I occasionally take on freelance opportunities.',
                content: "Have an exciting project where you need some help? Send me over a message, and let's chat."
            }
        }
    },
}
</script>
