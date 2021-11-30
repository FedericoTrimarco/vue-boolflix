<template>
    <main class="container mt-3">
        <cardProp
            v-for="movie in arrayMovies" :key="movie.id"
            :image="movie.poster_path"
            :title="movie.title"
            :originalTitle="movie.original_title"
            :lang="movie.original_language"
            :vote="movie.vote_average"
        />
        <cardProp
            v-for="serie in arraySeries" :key="serie.id"
            :image="serie.poster_path"
            :title="serie.name"
            :originalTitle="serie.original_name"
            :lang="serie.original_language"
            :vote="serie.vote_average"
        />
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
        arraySeries: Array,
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