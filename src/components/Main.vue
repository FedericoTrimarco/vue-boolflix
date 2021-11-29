<template>
    <main class="container border mt-3">
        <cardProp 
            v-for="(movie, index) in arrayMovies" :key="`${index}`"
            :ArrayMovies="movie"
            :title="movie.title"
            :originalTitle="movie.original_title"
            :lang="movie.original_language"
            :vote="movie.vote_average"
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
    }
}

</script>

<style scoped lang="scss">
@import '@/style/utilities';

</style>