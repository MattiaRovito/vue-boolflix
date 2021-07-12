<template>
  <div class="d-flex justify-content-end my-3">
      <input type="text" class="form-control input mt-2" placeholder="Cerca" v-model.trim="inputText">

      <button class="btn btn-success mx-2 mt-2" @click.prevent="$emit('searchMovies',inputText)">Cerca</button>
       <button type="submit" class="btn btn-danger mx-1 mt-2" @click.prevent="resetSearch">Reset</button>
  </div>
</template>

<script>
export default {
    name:'Search',
    data() {
        return {
            inputText:''
        }
    },
    methods: {
        resetSearch(){
           this.inputText = '';
            this.$emit('searchMovies',this.inputText);            
            
        }
    }
}
</script>

<style lang="scss" scoped>

.input
{
    width: 40%;    
}

</style>