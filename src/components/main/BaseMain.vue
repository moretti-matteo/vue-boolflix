<template>
    <main>
        <SectionMovies v-if="data.movies.length > 0" :movies="data.movies"></SectionMovies>
        <SectionSeries v-if="data.series.length > 0" :series="data.series"></SectionSeries>
    </main>
</template>

<script>
import SectionMovies from '../section-card/SectionMovies.vue';
import data from '../../shared/data.js';
import SectionSeries from '../section-card/SectionSeries.vue';

export default {
    name: "BaseMain",
    components: { SectionMovies: SectionMovies, SectionSeries },
    data() {
        return {
            data
        }
    }
}
</script>


<style lang="scss">
main {
    margin-top: 20px;
    margin-bottom: 20px;
    padding: 5px;

    &>*:last-child {margin-top: 50px;}
}
</style>