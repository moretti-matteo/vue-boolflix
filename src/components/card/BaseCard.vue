<template>
    <div class="card">
        <img :src="getPoster(poster)">
        <div class="card-hover">
            <div class="info-movie">
                <div v-if="title">
                    <h4>Titolo:</h4>{{ title }}
                </div>

                <div v-if="originalTitle">
                    <h4>Titolo originale:</h4>{{ originalTitle }}
                </div>

                <div>Vote:
                    <span v-for="n in 5" :key="n">
                        <i v-if="n <= vote" class='fa-solid fa-star'></i>
                        <i v-else class='fa-regular fa-star'></i>
                    </span>
                </div>

                <div v-if="overview">
                    <h4>Overview:</h4>{{ overview }}
                </div>
            </div>

        </div>
    </div>
</template>

<script>
export default {
    name: 'BaseCard',
    props: {
        title: String,
        originalTitle: String,
        overview: String,
        poster: String,
        vote: Number
    },
    methods: {
        getPoster(url) {
            return url ? ('https://image.tmdb.org/t/p/w342/' + url) : "https://upload.wikimedia.org/wikipedia/commons/thumb/6/65/No-Image-Placeholder.svg/1665px-No-Image-Placeholder.svg.png";
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../../assets/style/mixins.scss';



.card {
    width: calc(100% / 6 - 20px);
    position: relative;
    font-size: 0.9rem;

    @media screen and(max-width:992px) {
        & {
            width: calc(100% / 4 - 20px);
        }
    }

    @media screen and(max-width:600px) {
        & {
            width: calc(100% / 2 - 20px);
        }
    }

    @media screen and(max-width:400px) {
        & {
            width: calc(100% - 20px);
        }
        
    }

    img {
        width: 100%;
        height: 100%;
        display: block;
    }

    &:hover .card-hover {
        display: block;
        background: var(--color-black);
        overflow: auto;
        cursor: pointer;
    }

    .card-hover {
        display: none;
        @include pos-abs();

        .info-movie {
            color: white;
            background-color: var(--color-black);
            height: 100%;
            padding: 5px;

        }


    }
}
</style>