<script setup>
import Heros from '../views/section/Heros.vue'
import Portopolio from './section/Portopolio.vue'
import ContactUs from './section/ContactUs.vue'
import TheWelcome from '../components/TheWelcome.vue'
const props = defineProps(['name']);
const data = {
  title: "Hi, I'am Rizwan Gustama Front End Developer.",
  content: "I'm also a front-end developer and general doodle maker with a keen interest in creating attractive UIs, bringing products to life. interested in javascript and typescript"
}

</script>

<template>
  <Heros :title="data.title" :content="data.content"/>
  <Portopolio/>
  <ContactUs/>
</template>
