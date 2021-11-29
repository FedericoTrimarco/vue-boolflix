<template>
  <main class="container border mt-3">
        <ul class="border ms-1 mt-3" v-for="(movie, index) in ArrayMovies" :key="`${index}`">
            <li><strong>Titolo:</strong> {{ movie.title }}</li>
            <li><strong>Titolo Originale:</strong> {{ movie.original_title }}</li>
            <li><strong>Lingua:</strong> {{ movie.original_language }}</li>
            <li><strong>Voto:</strong> {{ movie.vote_average }}</li>
        </ul>
  </main>
</template>

<script>
// import axios from 'axios';
export default {
    name: 'Main',
    props:{
        ArrayMovies: Array,
    }
}

</script>

<style scoped lang="scss">
@import '@/style/utilities';

</style>