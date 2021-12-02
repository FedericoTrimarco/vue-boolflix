<template>
  <div id="app">
    <Header @search="searchMovieSeries"/>
    
    <main class="pt-5 border">
      <!-- SERIE TV / FILM -->
      <div v-if="MainMoviesList.length !== 0 && MainSeriesList.length !== 0">
        <!-- film -->
        <div class="tv-movie-list d-flex justify-content-center align-items-center">
          <img src="./assets/small-logo.png" alt="small-logo">
          <h1 class="text-white ms-1" v-show="MainMoviesList.length !== 0">MOVIE</h1>
        </div>
        <MainList :arrayList="MainMoviesList"/>
        <!-- serie -->
        <div class="tv-movie-list d-flex justify-content-center align-items-center">
          <img src="./assets/small-logo.png" alt="small-logo">
          <h1 class="text-white ms-1" v-show="MainSeriesList.length !== 0">SERIE</h1>
        </div>
        <MainList :arrayList="MainSeriesList"/>
      </div>

      <div v-else class="border text-center list-not-found h-100vh">
        <img src="./assets/Boolflix-big-logo.png" alt="logo" class="border ">
      </div>
    </main>
  </div>
</template>

<script>
import axios from 'axios';
import Header from '@/components/Header.vue'
import MainList from '@/components/MainList.vue'
export default {
  name: 'App',
  components: {
    Header,
    MainList,
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
@import '@/style/variables';
.tv-movie-list{
  text-align: center;
  margin: 50px 0;
  letter-spacing: 5px;
}
.list-not-found{
  background-image: url('./assets/cinema-bg.jpg');
  background-size: cover;
}


</style>
