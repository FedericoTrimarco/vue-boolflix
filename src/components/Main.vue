<template>
    <main class="container mt-3">
        <cardProp
            v-for="movie in arrayMovies" :key="movie.id"
            :title="movie.title"
            :originalTitle="movie.original_title"
            :lang="movie.original_language"
            :vote="movie.vote_average"
        />
        <cardProp
            v-for="serie in arraySeries" :key="serie.id"
            :name="serie.name"
            :originalName="serie.original_name"
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