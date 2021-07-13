<template>
  <main>
      <div class="container">
          <div class="search">
              <h2>Hai cercato: {{capitalize(campoRicerca)}} </h2>
              <div class="cards">
                  <!-- <Card  v-for="film in films" :key="film.id" :info="film"/> -->
                    <div class="cards">
                        <div v-for="(film, index) in films" :key="index">
                            <ul>
                                <li>Titolo: {{film.title}}</li>
                                <li>Titolo originale: {{film.original_title}}</li>
                                <li>Lingua: {{film.original_language}}</li>
                                <li>Voto: {{film.vote_average}}</li>
                            </ul>
                        </div>
                    </div>  
              </div>
          </div>
      </div>
  </main>
</template>

<script>
import Card from '@/components/Card.vue';

export default {
    name: 'Main',
    component : {
        Card,
    },
    props : {
        films: Array,
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

</style>