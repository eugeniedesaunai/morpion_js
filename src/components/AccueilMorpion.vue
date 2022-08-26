<template>
  <section class="texteCenter spaceAround tailleMax">
    <input class="designBoutton" type="button" value="Morpion 1">
    <input class="designBoutton" type="button" value="Règles">
  </section>

</template>

<script>

export default {
  name: 'AccueilMorpion',
  props: {

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.spaceAround {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}
</style>
