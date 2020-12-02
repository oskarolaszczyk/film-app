<template>
  <div class="hr"></div>
  <h1>Movie database</h1>
  <div id="tableFilms" ref="table">
    <table class="table-condensed table-hover">
      <thead>
      <tr>
        <th>Title</th>
        <th>Production Year</th>
        <th>Cast</th>
        <th>Genres</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="movie in dataFromEvent.slice(0, this.n)" :key="movie.title">
        <td>{{ movie.title }}</td>
        <td>{{ movie.year }}</td>
        <td>{{ movie.cast.join(', ') }}</td>
        <td>{{ movie.genres.join(', ') }}</td>
      </tr>
      </tbody>
    </table>
    <div>
      <button class="btn btn-info col-sm-12" type="button" v-on:click="more()">More</button>
    </div>
  </div>
</template>

<script>
  export default {
    name: "MovieTable",
    data() {
      return {
        n: 10,
      }
    },
    props: {
      dataFromEvent: Array,
    },
    
    methods: {
      more: function () {
        this.n += 10;
      },

    }
  }
</script>

<style scoped>
  table {
    width: 100%;
  }

  button {
    margin-top: 20px;
  }
</style>

