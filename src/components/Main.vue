<template>
  <main>
      <div class="container">
          <div class="search p-2">
                <h3 class="px-3"><strong>Hai cercato:</strong> {{capitalize(campoRicerca)}} </h3>
            
                <div class="d-flex flex-wrap">
                    
                        <Card  v-for="film in films" :key="film.id" :info="film" :img="film.poster_path" :vote="film.vote_average" class="col-4"/>
                        <!-- per i telefilm possiamo usare sempre :info -->         
                    
                    
                </div>
                <div class="d-flex flex-wrap">
                    
                    <Card  v-for="movie in movies" :key="movie.id" :info="movie" :img="movie.poster_path" :vote="movie.vote_average" class="col-4"/>
                 
                </div>
          </div>
      </div>
  </main>
</template>

<script>
import Card from '@/components/Card.vue';

export default {
    name: 'Main',
    components : {
        Card,
    },
    props : {
        films: Array,
        movies: Array,
        campoRicerca: String,
    },
    methods :{
        capitalize(string) {
           
            return string.charAt(0).toUpperCase() + string.slice(1);
        },

    }
}
</script>

<style lang="scss" scoped>
main
{
        
    background-color: black;
    overflow-y: scroll;
    color: white;
    
   

    .container
    {
        height: calc(100vh - 90px);
        
        
    }
}


</style>