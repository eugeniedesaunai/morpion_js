<template>
  <Push>
    <ReglesMorpion> </ReglesMorpion>
  </Push>
  <main class="tailleMax flexColumn " id="page-wrap">
    <h1 class="texteCenter neon">Morpion</h1>
    <section class="spaceAround padding flexColumn texteCenter">
      <PlancheJeu :joueurs="joueurs">
      </PlancheJeu>
      <JoueursPoints @click="retourAccueil"></JoueursPoints>
    </section>
  </main>
</template>

<script>
import ReglesMorpion from './ReglesMorpion.vue';
import JoueursPoints from './JoueursPoints.vue';
import { Push } from 'vue3-burger-menu';
import PlancheJeu from './PlancheJeu.vue';

export default {
  name: "PremierMorpion",
  data() {
    return {
    }
  },
  props: {
    joueurs: Array,
  },
  components: { ReglesMorpion, Push, PlancheJeu, JoueursPoints },
  methods: {
    retourAccueil() {
      this.$emit('retourAccueil')
    },
    submit() { },
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
* {
  box-sizing: border-box;
}

h1 {
  font-size: 50px !important;
  margin: 0 !important;
  margin-top: 0.5rem !important;
  margin-left: 0.9em !important;
  color: #f07171;
  text-shadow: 0px 0px 10px #f07171;
}

section {
  height: 100vh;
}

.padding {
  padding: 2vw;
}


@media(min-width: 768px) {
  .spaceAround {
    display: flex;
    justify-content: space-around;
  }

  h1 {
    font-size: 85px !important;
    margin: 0 !important;
  }
}
</style>
