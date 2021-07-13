<template>
  <div class="card">
    <ul>
      <li>Titolo: {{info.title}}</li>
      <li>Titolo originale: {{info.original_title}}</li>
      <li>Lingua: {{info.original_language}}</li>
      <li>Voto: {{info.vote_average}}</li>
    </ul>
  </div>
</template>

<script>
export default {
    name : "Card",
    props: ["info"]
}
</script>

<style lang="scss" scoped>

</style>