<template>
    <header>
        
        <div class="container flex justify-content-end nav p-3">
            
            <h1 class="logo mt-2 mx-3 fw-bold"><strong class="red">Bool</strong><strong>flix</strong></h1>
            <!-- <input
            type="text"
            placeholder="Cerca i tuoi film e serie tv"
            v-model="search"
            @keyup="$emit('ricerca', search)"
            class="mt-3 form-control"> -->
            
            <!-- al posto del keyup si può usare il bottone con il @click -->
            
            <input
            type="text"
            placeholder="Cerca i tuoi film e serie tv"
            v-model="search"
            class="mt-3 form-control">
    
            <button
            type="submit"
            class="btn btn-primary mx-2 mt-3 align-middle"
            @click.prevent="$emit('ricerca', search)"
            >Cerca
            </button>

            <button 
            type="submit" 
            class="btn btn-warning mx-1 mt-3" 
            @click.prevent="resetSearch">Reset
            </button>       
               
     
            
        </div>

    </header>

</template>

<script>

export default {
    name:'Header',
    data () {
        return {
            search :''

        }
    },
    methods : {
        resetSearch(){
            this.search = '',
            this.$emit('ricerca', this.search)
        }
    }
}
</script>

<style lang="scss" scoped>
header
{
    background-color: #202020;



    
    .nav
    {
        height: 90px;


        .red
        {
            color: red;
        }

        input
        {
            height: 40px;
            width: 20%;
            transition: width 1s;

            &:hover
            {
                width:25%;
            }
        }
    }
    .logo
    {

        color:white
    }
    button
    {
        height:40px;
    }
}


</style>


 transition: width 2s;
}

.searchicon:hover~.search{

}