<template>
  <SearchEngine @search-event="handleAppEvent"/>
  <MovieTable :dataFromEvent='eventData' />
  <MovieByGenre/>
  <MovieByCast/>

</template>

<script>
import MovieTable from './components/MovieTable.vue'
import SearchEngine from './components/SeachEnigne.vue'
import MovieByCast from './components/MovieByCast.vue';
import MovieByGenre from './components/MovieByGenre.vue'
import films from './assets/movies.json'

export default {
  name: 'App',
  components: {
    MovieTable,
    SearchEngine,
    MovieByCast,
    MovieByGenre
  },
  data: function(){
    return {
      eventData: films
    }
  },
    methods: {
    handleAppEvent: function(data) {
      this.eventData = data;
    }
  }
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
