<template>
    <header>
        <form @submit.prevent="cerca(query)">
            <input type="text" placeholder="inserisci serie da cercare" v-model="query" required>
            <button type="submit">Cerca</button>
        </form>
        <ul v-if="films.length > 0">
            <li v-for="film in films" :key="film.id">{{ film.title }} - {{ film.original_title }} -
                {{ film.original_language }} - {{ film.vote_average }}</li>
        </ul>
    </header>
</template>

<script>
import axios from 'axios';
export default {
    name: 'BaseHeader',
    data() {
        return {
            query: "",
            films: []
        }
    },
    methods: {
        cerca(q) {
            console.log(q);
            axios.get('https://api.themoviedb.org/3/search/movie', {
                params: {
                    api_key: "96ef12b1482064f51635d11a49c37c3f",
                    query: q,
                    language: 'it-IT'
                }
            }).then(resp => {
                console.log(resp.data.results);
                this.films = (resp.data.results);
            }).catch(error => console.log(error));
        }
    }
}
</script>

<style scoped>
header {}
</style>