<script>
import axios from 'axios';
export default {
    data() {
        return {
            dataArticle: [],
        }
    },

    mounted() {
        axios.get('https://newsapi.org/v2/top-headlines?country=us&category=technology&apiKey=03b7655a4ea2402fbf44302b96651440')
            .then(response => {
                this.dataArticle = response.data.articles;
                console.log(response.data.articles);
            })
            .catch(error => {
            console.log(error);
        })
    },
}
</script>

<template>
    <div>
        <h1>Ini adalah halaman blog</h1>
        <div class="container">
            <div class="grid grid-cols-4 gap-6">
                <a :href="item.url" v-for="(item, index) in dataArticle" :key="index">
                    <img :src="item.urlToImage == null ? 'https://images.unsplash.com/photo-1631155989897-961b8fe3aba4?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1887&q=80' : item.urlToImage" alt="">
                    <h1>{{ item.title }}</h1>
                    <p>{{ item.publishedAt }}</p>
                </a>
                
            </div>
        </div>
    </div>

</template>