<template>
  <h1>Search engine</h1>
  <form>
    <div class="form-group">
      <label for=inputTitle>Title</label>
      <input type="text" v-model="inputTitle" class="form-control" placeholder="Enter a title or fragment of the movie title"/>
    </div>
    <div class="form-group row">
      <label class="col-sm-4 col-form-label" for="inputProductionFrom">Production year from:</label>
      <div class="col-sm-8">
        <input type="text" v-model="inputProductionFrom" class="form-control"  placeholder="A natural number from the range 1900-2019 "/>
      </div>
    </div>
    <div class="form-group row">
      <label class="col-sm-4 col-form-label" for="inputProductionTo">Production year from:</label>
      <div class="col-sm-8">
        <input type="text" v-model="inputProductionTo" class="form-control" placeholder="A natural number from the range 1900-2019"/>
      </div>
    </div>
    <div class="form-group">
      <label for="inputCast">Cast</label>
      <input type="text" v-model="inputCast" class="form-control" placeholder="First name and last name"/>
    </div>
    <div>
      <button class="btn btn-info col-sm-12" type="button" v-on:click="search">Search</button>
    </div>
  </form>
</template>

<script>
  import movies from '../assets/movies.json';
  import _ from 'underscore'

  export default {
    name: "SearchEngine",
    data: function () {
    return {
      movies: movies,
      inputTitle: "",
      inputProductionFrom: "",
      inputProductionTo: "",
      inputCast: "",
  }
  },
    methods: {
      search: function () {
        let that = this;
        let moviesBySearch = this.movies
        moviesBySearch = _.filter(this.movies, function (movie) {

            let isInputTitle = that.inputTitle === "" || movie.title.toLowerCase().includes(that.inputTitle.toLowerCase())
            let isInputProductionFrom = that.inputProductionFrom === "" || movie.year >= that.inputProductionFrom 
            let isInputProductionTo = that.inputProductionTo === "" || movie.year <= that.inputProductionTo
            let isInputCast = that.inputCast === "" || movie.cast.includes(that.inputCast)

          if (isInputTitle && isInputProductionFrom && isInputProductionTo && isInputCast) {
              return true;
          } 
          return false;
          });
          
        this.$emit("search-event", moviesBySearch);
      },
  },
};
</script>

<style scoped>
  h1 {
    margin-bottom: 20px;
  }
  label {
    font-weight: 700;
  }
</style>


