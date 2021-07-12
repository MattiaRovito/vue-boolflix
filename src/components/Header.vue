<template>
  <section class="container">
      <div class="row nav">
          <div class="col-12">
              <Search @searchMovies ="list"/>
          </div>
      </div>
  </section>
</template>

<script>
import axios from 'axios';
import Search from '@/components/Search.vue';
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

    .nav
    {
        // background-color: blue;
        height: 90px;
        background-color: #020202;
    }



</style>