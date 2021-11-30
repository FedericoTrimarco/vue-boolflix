<template>
    <main class="container mt-3">
        <div v-if="arrayMovies.length > 0">
            <cardProp
                v-for="movie in arrayMovies" :key="movie.id"
                :ArrayMovies="movie"
                :title="movie.title"
                :originalTitle="movie.original_title"
                :lang="movie.original_language"
                :vote="movie.vote_average"
            />
        </div>
        <div v-else class="loading">
            <h1>no results found</h1>
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
    }
</style>