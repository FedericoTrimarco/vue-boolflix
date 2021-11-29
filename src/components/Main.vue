<template>
    <main class="container mt-3">
        <div v-if="arrayMovies.length > 0">
            <cardProp
                v-for="(movie, index) in arrayMovies" :key="`${index}`"
                :ArrayMovies="movie"
                :title="movie.title"
                :originalTitle="movie.original_title"
                :lang="movie.original_language"
                :vote="movie.vote_average"
            />
        </div>
        <div v-else class="loading">
            <h1>no results found</h1>
            <i class="load-icon fas fa-circle-notch my-5"></i>
        </div>
    </main>
</template>

<script>
import cardProp from '../components/cardProp.vue'
export default {
    name: 'Main',
    components: {
        cardProp,
    },
    props:{
        arrayMovies: Array,
    }
}

</script>

<style scoped lang="scss">
@import '@/style/utilities';

    .loading{
        h1{
            font-size: 50px;
        }
        .load-icon{
            font-size: 50px;
            animation: rotation 1.2s linear infinite;
            
            @keyframes rotation {
                0%{
                    transform: rotate(-360deg);
                }
            }
        }
    }
</style>