<template>
  <div id="app">
    <Header @search="searchMovieSeries"/>

    <Main :arrayMovies="MainMoviesList" :arraySeries="MainSeriesList"/>
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
      MainSeriesList: [],
      searchFilmSeries: '',
    }
  },
  created() {
    this.genMovieSeries();
  },

  methods: {
    genMovieSeries(){
      if(this.searchFilmSeries != ''){
        axios.get('https://api.themoviedb.org/3/search/movie', {
          params:{
            api_key: 'd6dd0dbacc670d77c1aae585ef4c4f9a',
            query: this.searchFilmSeries,
          }
        })
        .then(el => {
          this.MainMoviesList = el.data.results;
        })
        .catch(error => console.log(error))

        axios.get('https://api.themoviedb.org/3/search/tv', {
          params:{
            api_key: 'd6dd0dbacc670d77c1aae585ef4c4f9a',
            query: this.searchFilmSeries,
          }
        })
        .then(el => {
          this.MainSeriesList = el.data.results;
        })
        .catch(error => console.log(error))
        
      }

    },
      
    searchMovieSeries(text) {
      this.searchFilmSeries = text;
      this.genMovieSeries()
    },
  }
}
</script>

<style lang="scss">
@import '@/style/globals';
@import '@/style/utilities';

</style>
