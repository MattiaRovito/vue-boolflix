<template>
  <div class="card">
    <div>
      <div>
        <!-- == null ovvero se non c'è stampi info.name, altrimenti stampi info.title -->
        <!-- oppure si può usare l'or || -->
        <ul class="p-2 mx-2">
          <li>
              <img :src="posterImg" :alt="info.title" class="poster">
          </li>



          <li>
            <span class="fw-bold">Titolo</span>: 
            {{info.title == null ? info.name : info.title}}
          </li>
          
          <li>
            <span class="fw-bold">Titolo originale</span>: 
            {{info.original_title || info.original_name}}
          </li>
          
          <li v-if="bandiere.includes(info.original_language)">
            <span class="fw-bold">Lingua</span>: 
            
            <!-- grazie al require riesco ad importare le immagini. Senza, il sistema non riesce a definire il percorso dove andare a prendere le determinate immagini. -->
            <img :src="require(`../assets/img/${info.original_language}.png`)" 
                  :alt="info.original_language"
                  class="bandiere">
          </li>

          <li v-else>

            <span class="fw-bold">Lingua</span>: 
            {{info.original_language}}
            
            <img :src="require(`../assets/img/${info.original_language}.png`)" 
                  :alt="info.original_language"
                  class="bandiere">
          </li>
          
          <li>
            <span class="fw-bold">Voto</span>: 
            {{info.vote_average}}
          </li>
        </ul>
      </div>
    </div>
    
  </div>
</template>

<script>
export default {
    name : "Card",
    props: {
      info : String,
      img : String
      },
    data () {
      return {
        bandiere : ["en", "it", "es", "fr"],  
        posterImg: '',
      } 
    },
    created (){
      this.addPoster()
    },
    methods : {
      addPoster(){
       this.posterImg = "https://image.tmdb.org/t/p/" + "w342" + this.img;
      }
    }
}
</script>

<style lang="scss" scoped>

  ul{
    margin-top: 10px;
    li{
      list-style: none;

    }
  }
   .bandiere {
        width: 2%;
        margin-bottom: 2px;
      }
</style>