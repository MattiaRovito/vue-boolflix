<template>
  <main>
      <div class="container">
          <div class="search">
              <h2>Hai cercato: {{capitalize(campoRicerca)}} </h2>
              <div class="cards">
                  <Card  v-for="film in films" :key="film.id" :info="film"/>
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