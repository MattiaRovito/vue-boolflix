<template>
  <main>
      <div class="container">
          <div class="search p-2">
              <h3><strong>Hai cercato:</strong> {{capitalize(campoRicerca)}} </h3>
              <div class="cards mt-2">
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
main
{
        
    background-color: black;
    overflow-y: scroll;
    
    h3
    {
        color: white;
    }

    .container
    {
        height: calc(100vh - 90px);
        
        
    }
}


</style>