<template>
    <div class="hr"></div>

      <h1>Movies by cast</h1>
        <ol v-for="cast in casts" :key="cast">
            <h2>{{ cast }}</h2>
            <li v-for="movie in getMoviesByCast(cast)" :key="movie">{{ movie.title }}</li>     
      </ol>
</template>

<script>
import movies from '../assets/movies.json';
import _ from "underscore";

export default {
  name: "MovieByCast",
  data() {
    return {
      movies: movies,
      casts: [],
    };
  },
methods: {
      getRandomMovies: function () {
      let randomMovies = this.movies;
      randomMovies.sort(() => Math.random() - 0.5);

      return randomMovies.slice(0, 25);
    },

    getMoviesByCast: function (cast) {
      let moviesByCast = _.filter(this.movies, function (movie) {
        for (let i in movie.cast) {
          if (movie.cast[i] === cast) {
            return true;
          }
        }
        return false;
      });

      moviesByCast = _.sortBy(moviesByCast, function (movie) {
        return movie.title;
      });

      return moviesByCast;
    },

    getCasts: function () {
      let casts = [];
      for (let movie in this.movies) {
        for (let cast in this.movies[movie].cast) {
            casts.push(this.movies[movie].cast[cast]);
          }
        }
      this.casts = _.unique(casts);
    },
  },

  mounted() {
    this.movies = this.getRandomMovies();
    this.getCasts();
  },

};
</script>

<style scoped>

h2, li {
      text-align: left;
}

</style>