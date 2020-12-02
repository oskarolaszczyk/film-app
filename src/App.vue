<template>
  <SearchEngine @search-event="handleSearchEvent"/>
  <MovieTable :dataFromEvent='eventData' />
  <MovieByGenre/>
  <MovieByCast/>
  <Footer/>

</template>

<script>
  import MovieTable from './components/MovieTable.vue'
  import SearchEngine from './components/SeachEnigne.vue'
  import MovieByCast from './components/MovieByCast.vue';
  import MovieByGenre from './components/MovieByGenre.vue'
  import Footer from './components/Footer.vue'
  import movies from './assets/movies.json'

  export default {
    name: 'App',
    components: {
      MovieTable,
      SearchEngine,
      MovieByCast,
      MovieByGenre,
      Footer
    },
    data: function(){
      return {
        eventData: movies
      }
    },
      methods: {
      handleSearchEvent: function(data) {
        this.eventData = data;
      }
    }
  }
</script>

<style>
  h1 {
    margin-top: 30px;
    margin-bottom: 20px;
    font-size: 35px;
    text-transform: uppercase;
  }

  h2 {
    margin-top: 20px;
    font-size: 25px;
    text-transform: uppercase;
  }

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
