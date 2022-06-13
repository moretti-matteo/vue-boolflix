<template>
    <section>
        <h1>Movies:</h1>
        <div class="container">
            <BaseCard v-for="movie in movies" :key="movie.id" :title="movie.title" :originalTitle="movie.original_title"
                :overview="movie.overview" :poster="movie.poster_path" :vote="movie.vote_average" :language="movie.original_language" />
        </div>


    </section>
</template>

<script>
import BaseCard from '../card/BaseCard.vue';
export default {
    name: "SectionMovies",
    props: {
        movies: []
    },
    components: { BaseCard }
}
</script>
    
<style lang="scss">


section {
    h1 {
        color: white;
    }
}
</style>