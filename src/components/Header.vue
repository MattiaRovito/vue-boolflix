<template>
    <header>
        <div class="container flex nav justify-content-between p-3">
            <h1 class="logo mt-1 fw-bold"><strong class="red">Bool</strong><strong>flix</strong></h1>

            <input 
            type="text" 
            placeholder="Cerca i tuoi film e serie tv"
            v-model="search"
            @keyup="$emit('ricerca', search)"
            class="mt-3 form-control">
            <!-- al posto del keyup si può usare il bottone con il @click -->
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
    }
}
</script>

<style lang="scss" scoped>

    .nav
    {
        height: 90px;
        background-color: #020202;

        .red
        {
            color: red;
        }

        input
        {
            height: 30px;
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



</style>


 transition: width 2s;
}

.searchicon:hover~.search{
  
}