<template>
    <header>
        <div class="container">
            <h1>Boolflix</h1>
            <form @submit.prevent="cerca(query)">
                <input type="text" placeholder="Search Movies or Series TV" v-model="query" required>
                <button type="submit"><i class='fa-solid fa-magnifying-glass'></i></button>
            </form>
        </div>
    </header>
</template>

<script>
import axios from 'axios';
import data from '../../shared/data';

export default {
    name: 'BaseHeader',
    data() {
        return {
            data,
            query: "",
        }
    },
    methods: {
        cerca(q) {
            console.log(q);

            //RECUPERO I FILM
            axios.get('https://api.themoviedb.org/3/search/movie', {
                params: {
                    api_key: "96ef12b1482064f51635d11a49c37c3f",
                    query: q,
                    language: 'it-IT'
                }
            }).then(resp => {

                this.data.movies = resp.data.results;
                this.data.movies.forEach(movie => movie.vote_average = this.fixVote(movie.vote_average));
            }).catch(error => console.log(error));

            //RECUPERO LE SERIE TV
            axios.get('https://api.themoviedb.org/3/search/tv', {
                params: {
                    api_key: "96ef12b1482064f51635d11a49c37c3f",
                    query: q,
                    language: 'it-IT'
                }
            }).then(resp => {
                console.log(resp);
                this.data.series = resp.data.results;
                this.data.series.forEach(serie => serie.vote_average = this.fixVote(serie.vote_average));

            }).catch(error => console.log(error));

            this.query = "";
        },
        fixVote(vote) {
            return Math.ceil(vote / 2);
        }
    }
}
</script>

<style lang="scss" scoped>
header {
    background: #222;
    padding: 15px 0;

    @media screen and(max-width:600px) {
        & {
            .container {
                flex-direction: column;
            }
        }

    }

    input[type="text"],
    button {
        padding: 5px 10px;

    }

    button:hover {
        cursor: pointer;
    }

}

.container {
    color: var(--color-red);
    align-items: center;
    justify-content: space-between;
}

img {
    width: 100px;
}
</style>