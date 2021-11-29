<template>
  <div id="app">
    <Header @search="searchMovie"/>

    <Main :arrayMovies="MainMoviesList"/>
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
      MainMoviesList : [],
      searchFilm: '',
    }
  },
  created() {
    this.genMovie();
  },

  methods: {
    genMovie(){
      if(this.searchFilm != ''){
        axios.get('https://api.themoviedb.org/3/search/movie', {
          params:{
            api_key: 'd6dd0dbacc670d77c1aae585ef4c4f9a',
            query: this.searchFilm,
          }
        })
          .then(el => {
            this.MainMoviesList = el.data.results;
          })
          .catch(error => console.log(error))
        }
        else{
          this.MainMoviesList = [];
        }

      },
      
    searchMovie(text) {
      this.searchFilm = text;
      this.genMovie()
    },
  }
}
</script>

<style lang="scss">
@import '@/style/globals';
@import '@/style/utilities';

</style>
