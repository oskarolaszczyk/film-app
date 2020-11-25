<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <SearchEngine @search-event="handleAppEvent"/>
  <MovieTable :dataFromEvent='eventData' />

</template>

<script>
import MovieTable from './components/MovieTable.vue'
import SearchEngine from './components/SeachEnigne.vue'
import films from './assets/movies.json'

export default {
  name: 'App',
  components: {
    MovieTable,
    SearchEngine
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
