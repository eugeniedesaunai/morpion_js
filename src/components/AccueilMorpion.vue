<template>
  <section class=" spaceAround tailleMax">
    <img class="tailleImg" src="../img/morpion.png" alt="">
    <input class="designBoutton texteCenter red" type="button" value="Jouer" @click="morpion">
    <ReglesMorpion> </ReglesMorpion>
  </section>

</template>

<script>
import ReglesMorpion from './ReglesMorpion.vue'
export default {
  name: 'AccueilMorpion',
  components: { ReglesMorpion },
  props: {

  },
  methods: {

    morpion() {
      this.$emit('morpion')
    }

  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.spaceAround {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}

.tailleImg {
  width: 50vw;
  align-self: center;
}

@media(min-width: 768px) {
  .tailleImg {
    width: 40vw;
    align-self: center;
  }
}

@media(min-width: 1024px) {
  .tailleImg {
    width: 30vw;
    align-self: center;
  }
}
</style>
