<template>
  <main>
      <div class="container">
          <div class="search">
              <h2>Hai cercato: {{campoRicerca}} </h2>
              <div class="cards">
                  <Card v-for="film in films" :key="film.id" :info="film"/>
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
    }
}
</script>

<style lang="scss" scoped>

</style>