<template>
  <section class="texteCenter spaceAround">
    <input class="designButtonAccueil" type="button" value="Morpion 1">
    <input class="designButtonAccueil" type="button" value="Morpion 2">
    <input class="designButtonAccueil" type="button" value="Règles">
    <input class="designButtonAccueil" type="button" value="Connexion">
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
.texteCenter {
  text-align: center;
}

.designButtonAccueil {
  background-color: #2D3142;
  color: #D8D5DB;
  border-radius: 1.5rem;
}

.spaceAround {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}
</style>
