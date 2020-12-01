<template>
<form>
        <div>
            <label for=inputTitle>Tytuł</label>
            <input v-model="inputTitle" type="text" id=inputTitle placeholder="Podaj tytuł lub fragment tytułu movieu"/>
        </div>
        <div>
          <label for="inputProductionFrom">Rok produkcji od:</label>
          <div>
              <input v-model="inputProductionFrom" type="text" id=inputProductionFrom placeholder="Liczba naturalna z przedziału 1900-2019"/>
          </div>
        </div>
        <div>
            <label for="inputProductionTo">Rok produkcji do:</label>
            <div>
                <input v-model="inputProductionTo" type="text" id=inputProductionTo placeholder="Liczba naturalna z przedziału 1900-2019"/>
            </div>
        </div>
        <div>
          <label for="inputCast">Obsada</label>
          <input v-model="inputCast" type="text" id="inputCast" placeholder="Imię i nazwisko"/>
        </div>
        <div>
            <button
          type="button"
          v-on:click="search">
        Search
      </button>
        </div>
</form>
</template>

<script>
      import movies from '../assets/movies.json';
      import _ from 'lodash'

      export default {
            name: "SearchEngine",
            data: function () {
                  return {
                        movies: movies,
                        inputTitle: "",
                        inputProductionFrom: "",
                        inputProductionTo: "",
                        inputCast: "",
                        listEmitted: movies,
                  }
            },
            // TO-DO: poprawić czytelność kodu, pozmienać zmienne itp
             methods: {
    search: function () {
      let self = this;
      this.listEmitted = _.filter(this.movies, function (film) {
        if (
            (self.inputTitle === "" ||
                film.title.toLowerCase().includes(self.inputTitle.toLowerCase())) &&
            (film.year >= self.inputProductionFrom || self.inputProductionFrom === "") &&
            (film.year <= self.inputProductionTo|| self.inputProductionTo=== "")
        ) {
          if (self.inputCast === "") {
            return true;
          } else {
            for (let i = 0; i < film.cast.length; i++) {
              if (film.cast[i].toLowerCase() === self.inputCast.toLowerCase()) {
                return true;
              }
            }
          }
        }
        return false;
      });
      this.$emit("search-event", self.listEmitted);
    },
  },
};
</script>

<style scoped>
    
</style>


