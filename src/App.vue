// Note Personali

// All'interno dell'App.vue sono state create due components (Header e Main). Attraverso la funzione ricercaFilm() sono state effettuate due chiamate axios per i film e i telefilm (nei data() sono stati inseriti gli URL con i rispettivi array da popolare). Nella header sono stati creati gli input e i bottoni che, attraverso l'emit, andranno ad effettuare la ricerca mediante gli URL presenti nell'APP.vue. l'emit è stato quindi collegato nell'App.vue (@ricerca="ricercaFilm"). Per quanto riguarda il Main, dopo aver effettuato la ricerca, i due array (moviesArray e seriesArray) popolati, sono stati inviati tramite un props nella component Main. All'interno della component è stata creata un'altra component (Card) che, mediante sempre un props, ha permesso di stampare a schermo gli elementi voluti.


<template>
  <div id="app">
    <Header @ricerca="ricercaFilm"/>

    <Main :films="moviesArray" :movies="seriesArray" :campoRicerca="searchText" />
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
      apiTvURL: 'https://api.themoviedb.org/3/search/tv',
      key: 'bfcf208327aefb75b3731be9f3c9c913',
      language: 'it-IT',
      moviesArray : [],
      seriesArray : [],
      searchText : ''
    }
  }, 
  methods: {
    ricercaFilm(text){
      this.searchText = text;





      // axios
      //   .get(this.apiURL, {
      //     params : {
      //       api_key: this.key,
      //       language: this.language,
      //       query: text,
      //     }
      //   })
      //   .then(response=>{
      //     this.moviesArray = response.data.results;
      //   });

      //* più chiamate axios con il metodo all e spread
      
      //* Il metodo all prende un array all'interno dove posso specificare le due chiamate axios. 

      //* essendo le variabili costanti 

      const request = {
        params : {
              api_key: this.key,
              language: this.language,
              query: text,
            }
      };

      axios
        .all ([
          axios.get(this.apiURL, request),
          axios.get(this.apiTvURL, request)
        ])
        //* responseMovies e responseTv sono due segnaposti
        .then(axios.spread((responseMovies, responseTv) => {
            this.moviesArray = responseMovies.data.results;
            this.seriesArray = responseTv.data.results;
        }))




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




//Todo Milestone 2:
//* Trasformiamo la stringa statica della lingua in una vera e propria bandiera della nazione corrispondente, gestendo il caso in cui non abbiamo la bandiera della nazione ritornata dall’API (le flag non ci sono in FontAwesome). Allarghiamo poi la ricerca anche alle serie tv. Con la stessa azione di ricerca dovremo prendere sia i film che corrispondono alla query, sia le serie tv, stando attenti ad avere alla fine dei valori simili (le serie e i film hanno campi nel JSON di risposta diversi, simili ma non sempre identici).
//* Qui un esempio di chiamata per le serie tv:
//* https://api.themoviedb.org/3/search/tv?api_key=e99307154c6dfb0b4750f6603256716d&language=it_IT&query=scrubs




//TODO Milestone 3:
//* In questa milestone come prima cosa aggiungiamo la copertina del film o della serie al nostro elenco. Ci viene passata dall’API solo la parte finale dell’URL, questo perché poi potremo generare da quella porzione di URL tante dimensioni diverse. Dovremo prendere quindi l’URL base delle immagini di TMDB: https://image.tmdb.org/t/p/ per poi aggiungere la dimensione che vogliamo generare (troviamo tutte le dimensioni possibili a questo link: https://www.themoviedb.org/talk/53c11d4ec3a3684cf4006400) per poi aggiungere la parte finale dell’URL passata dall’API. Esempio di URL: https://image.tmdb.org/t/p/w342/wwemzKWzjKYJFfCeiB57q3r4Bcm.png