<template>
  <div id="app">
    <Header />

    <Main :ArrayMovies="MainMoviesList"/>
  </div>
</template>

<script>
import axios from 'axios';
import Header from '@/components/Header.vue'
import Main from '@/components/Main.vue'
export default {
  name: 'App',
  components: {
    Header,
    Main,
  },
  data(){
    return{
      MainMoviesList : null,
    }
  },
  created() {
    this.genMovie();
  },

  methods: {
    genMovie(){
      axios.get('https://api.themoviedb.org/3/search/movie', {
        params:{
          api_key: 'd6dd0dbacc670d77c1aae585ef4c4f9a',
          query: 'fantozzi',
        }
      })
        .then(el => {
          console.log(el.data.results);
          this.MainMoviesList = el.data.results;
        })
        .catch(error => console.log(error))
    },
  }
}
</script>

<style lang="scss">
@import '@/style/globals';
@import '@/style/utilities';

</style>
