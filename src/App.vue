<template>
  <div id="app">
    <Header @search="searchMovieSeries"/>
    
    <main class="pt-5 border">
      <!-- SERIE TV / FILM -->
      <div v-if="MainMoviesList.length !== 0 && MainSeriesList.length !== 0">
        <!-- film -->
        <h1 class="tv-movie-list text-white" v-show="MainMoviesList.length !== 0">MOVIE</h1>
        <MainList :arrayList="MainMoviesList"/>
        <!-- serie -->
        <h1 class="tv-movie-list text-white" v-show="MainSeriesList.length !== 0">SERIE TV</h1>
        <MainList :arrayList="MainSeriesList"/>
      </div>

      <div v-else class="border text-center list-not-found">
        <img src="./assets/Boolflix-big-logo.png" alt="logo" class="border ">
        <h1 class="pt-5"> GUARDA LE TUE SERIE TV / FILM PREFERITI DIRETTAMENTE DAL TUO DIVANO</h1>
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
.list-not-found h1{
  color: $primary-color;
}

</style>
