<template>
  <section class="container">
      <div class="row">
          <div class="col-12">
              <Search @searchMovies ="list"/>
          </div>
      </div>
  </section>
</template>

<script>
import axios from 'axios';
export default {
    name:'Header',
    components : {
        Search
    },
    data(){
        return {
            apiURL : 'https://api.themoviedb.org/3/search/movie',
            searchList: ''
        }
    },
    created (){
        this.getList();
    },
    computed:{

    },
    methods:{
        getList(){
            axios
                .get(this.apiURL)
                .then(res =>{
                    console.log(res.data);
                    this.searchList = res.data.response;
                    console.log(this.searchList);
                    
                })
        },
        searchFilm(searchInput){
            this.searchList = searchInput;
            // console.log('ciao', this.searchList);
        }
    }

}
</script>

<style lang="scss" scoped>

    .row
    {
        background-color: red;
        height: 400px;
    }



</style>