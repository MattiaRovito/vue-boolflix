<template>
  <div class="card">
    <div>
      <div>
        <ul class="p-2 mx-2">
          <li><span class="fw-bold">Titolo</span>: {{info.title}}</li>
          <li><span class="fw-bold">Titolo originale</span>: {{info.original_title}}</li>
          <li><span class="fw-bold">Lingua</span>: {{info.original_language}}</li>
          <li><span class="fw-bold">Voto</span>: {{info.vote_average}}</li>
        </ul>
      </div>
    </div>
    
  </div>
</template>

<script>
export default {
    name : "Card",
    props: ["info"]
}
</script>

<style lang="scss" scoped>

  ul{
    li{
      list-style: none;
    }
  }
</style>