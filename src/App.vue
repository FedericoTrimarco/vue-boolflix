<template>
  <div id="app">
    <Header @search="searchMovieSeries"/>
    
    <main class="pt-5 border">
      <!-- SERIE TV / FILM -->
      <div v-if="MainMoviesList.length !== 0 || MainSeriesList.length !== 0">
        <!-- film -->
        <TypologyTitle v-show="MainMoviesList.length !== 0" :mainArray="MainMoviesList" text="MOVIE"/>
        <MainList :arrayList="MainMoviesList"/>
        <!-- serie -->
        <TypologyTitle v-show="MainSeriesList.length !== 0" :mainArray="MainSeriesList" text="SERIE"/>
        <MainList :arrayList="MainSeriesList"/>
      </div>
        <!-- HOME -->
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
import TypologyTitle from '@/components/TypologyTitle.vue'
export default {
  name: 'App',
  components: {
    Header,
    MainList,
    TypologyTitle,
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
#app{
  background-image: url('./assets/bg-gray.png');
  background-size: cover;
  background-attachment: fixed;
  transition: background-image .5s linear 1s,
}
.list-not-found{
  background-image: url('./assets/cinema-bg.jpg');
  background-size: cover;
}


</style>
