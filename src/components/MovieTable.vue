<template>
  <div id="tableFilms" ref="table">
    <table>
      <thead>
      <tr>
        <th>Title</th>
        <th>Production Year</th>
        <th>Cast</th>
        <th>Genres</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="film in sliceView()" v-bind:key="film.title">
        <td>{{ film.title }}</td>
        <td>{{ film.year }}</td>
        <td>{{ film.cast.join(', ') }}</td>
        <td>{{ film.genres.join(', ') }}</td>
      </tr>
      </tbody>
    </table>
    <div>
      <button type="button" id="more" @click="moreMovies()">
        More
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "MovieTable",
  data() {
    return {
      n: 10,
      numberOfMovies: 10,
    }
  },
  props: {
    dataFromEvent: Array,
  },
  
  methods: {
    sliceView: function () {
      let films = this.dataFromEvent;
      return films.slice(0, this.n);
    },
    moreMovies: function () {
      this.n += this.numberOfMovies;
    },
  }
}
</script>

<style scoped>
#tableFilms {
      margin: 0 auto;
}
      tr:hover{
            background-color: #aaa;
      }
</style>

