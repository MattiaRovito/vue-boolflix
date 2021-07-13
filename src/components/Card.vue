<template>
  <div class="card">
    <ul>
      <li>Titolo: {{info.title}}</li>
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