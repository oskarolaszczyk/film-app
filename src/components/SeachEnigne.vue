<template>
<form>
        <div>
            <label for=inputTitle>Tytuł</label>
            <input type="text" id=inputTitle placeholder="Podaj tytuł lub fragment tytułu filmu"/>
        </div>
        <div>
          <label for="inputProductionFrom">Rok produkcji od:</label>
          <div>
              <input type="text" id=inputProductionFrom placeholder="Liczba naturalna z przedziału 1900-2019"/>
          </div>
        </div>
        <div>
            <label for="inputProductionTo">Rok produkcji do:</label>
            <div>
                <input type="text" id=inputProductionTo placeholder="Liczba naturalna z przedziału 1900-2019"/>
            </div>
        </div>
        <div>
          <label for="inputCast">Obsada</label>
          <input type="text" id="inputCast" placeholder="Imię i nazwisko"/>
        </div>
        <div>
            <input type="button" value="Szukaj"/>
        </div>
</form>
</template>

<script>
      export default {
      name: "SearchEngine"
      }
</script>

<style scoped>
     
</style>


