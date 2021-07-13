<template>
  <div id="app">
    <Header @ricerca="ricercaFilm"/>

    <Main :films="moviesArray"/>
  </div>
</template>

<script>
import axios from 'axios';
import Header from '@/components/Header.vue';
import Main from '@/components/Main.vue';

export default { 
  name: 'App',
  components: {
    Header,
    Main
  },
  data () {
    return {
      apiURL: 'https://api.themoviedb.org/3/search/movie', 
      key: 'bfcf208327aefb75b3731be9f3c9c913',
      language: 'it-IT',
      moviesArray : []
    }
  }, 
  methods: {
    ricercaFilm(text){
      axios
        .get(this.apiURL, {
          params : {
            api_key: this.key,
            language: this.language,
            query: text,
          }
        })
        .then(response=>{
          this.moviesArray = response.data.results;
        })
      //  console.log(text);
    }
  }
}
</script>

<style lang="scss">

@import '@/style/commons.scss';

</style>



//TODO Milestone 1:
//* Creare un layout base con una searchbar (una input e un button) in cui possiamo scrivere completamente o parzialmente il nome di un film. Possiamo, cliccando il bottone, cercare sull’API tutti i film che contengono ciò che ha scritto l’utente. Vogliamo dopo la risposta dell’API visualizzare a schermo i seguenti valori per ogni film trovato:
//* 1. Titolo
//* 2. Titolo Originale
//* 3. Lingua
//* 4. Voto