<template>
  <div id="app" class="d-flex flex-column">
    <Header @search="searchMovieSeries" @click="filter"/>
    
    <main class="pt-5 border flex-grow-1">
      <!-- SERIE TV / FILM -->
      <div v-if="MainMoviesList.length !== 0 || MainSeriesList.length !== 0">
        <!-- film -->
        <div v-show="link === 'Film' || link === 'Home'">
          <TypologyTitle :mainArray="MainMoviesList" text="MOVIE"/>
          <MainList :arrayList="MainMoviesList"/>
        </div>
        <!-- serie -->
        <div v-show="link === 'Serie Tv' || link === 'Home'">
          <TypologyTitle :mainArray="MainSeriesList" text="SERIE"/>
          <MainList :arrayList="MainSeriesList"/>
        </div>
      </div>
        <!-- HOME -->
      <div v-else class="border text-center list-not-found h-100vh">
        <img src="./assets/Boolflix-big-logo.png" alt="logo" class="border w-50 mt-3">
      </div>
    </main>
    <Footer />
  </div>
</template>

<script>
import axios from 'axios';
import Header from '@/components/Header.vue'
import MainList from '@/components/MainList.vue'
import TypologyTitle from '@/components/TypologyTitle.vue'
import Footer from '@/components/Footer.vue'
export default {
  name: 'App',
  components: {
    Header,
    MainList,
    TypologyTitle,
    Footer,
  },
  data(){
    return{
      MainMoviesList : [],
      MainSeriesList: [],
      searchFilmSeries: '',
      link: 'Home',
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
    filter(el){
      this.link = el;
    }
  }
}
</script>

<style lang="scss">
@import '@/style/globals';
@import '@/style/utilities';
@import '@/style/variables';
#app{
  flex-grow: 1;
  background-image: url('./assets/bg-gray.png');
  background-size: cover;
  background-position: center;
  background-attachment: fixed;
  transition: background-image .5s linear 1s,
}
.list-not-found{
  background-image: url('./assets/cinema-bg.jpg');
  background-size: cover;
  background-position: center;
}


</style>
