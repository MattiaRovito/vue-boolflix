<template>
    <header>
        <div class="container">
            <div class="logo">Boolflix</div>

            <input 
            type="text" 
            placeholder="Cerca i tuoi film e serie tv"
            v-model="search"
            @keyup="$emit('ricerca', search)">
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
    }



</style>