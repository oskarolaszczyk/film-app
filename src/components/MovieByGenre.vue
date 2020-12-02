<template>
      <div class="hr"></div>
      <h1>Movies by genre</h1>
            <ol v-for="genre in genres" :key="genre">
                  <h2>{{ genre }}</h2>
                  <li v-for="movie in getMoviesByGenre(genre)" :key="movie">{{ movie.title }}</li>
            </ol>
</template>

<script>
      import movies from '../assets/movies.json';
      import _ from "underscore";

      export default {
            name: "MovieByGenre",
            data() {
                  return {
                        movies: movies,
                        genres: [],
                  };
            },
            methods: {
                  getRandomMovies: function () {
                        let randomMovies = this.movies;
                        randomMovies.sort(() => Math.random() - 0.5);

                        return randomMovies.slice(0, 50);
                  },

                  getGenres: function () {
                        let genres = [];
                        for (let movie in this.movies) {
                              for (let genre in this.movies[movie].genres) {
                                    genres.push(this.movies[movie].genres[genre]);
                              }
                        }
                        this.genres = _.unique(genres);
                  },
                  getMoviesByGenre: function (genre) {
                        let moviesByGenre = _.filter(this.movies, function (movie) {
                        for (let i in movie.genres) {
                              if (movie.genres[i] === genre) {
                              return true;
                              }
                        }
                        return false;
                        });

                        moviesByGenre = _.sortBy(moviesByGenre, function (movie) {
                        return movie.title;
                  });

                  return moviesByGenre;
            },
            },

            mounted() {
                  this.movies = this.getRandomMovies();
                  this.getGenres();
            },

      };
</script>

<style scoped>
      h2, li {
            text-align: left;
      }
</style>