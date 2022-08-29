<template>
  <main class="width">
    <h1 class="texteCenter">Morpion {{ scorePremierJoueur }}</h1>
    <section class="spaceAround flex padding">
      <NeufCases @score="score" :joueurs="joueurs">
      </NeufCases>
      <ReglesMorpion> </ReglesMorpion>
    </section>
    <JoueursPoints @submit="submit" @click="retourAccueil" :joueurs="joueurs">
    </JoueursPoints>
  </main>
</template>

<script>
import NeufCases from './NeufCases.vue';
import ReglesMorpion from './ReglesMorpion.vue';
import JoueursPoints from './JoueursPoints.vue';

export default {
  name: "PremierMorpion",
  data() {
    return {
      current_player: 0,
    }
  },
  props: {
    joueurs: Array,
  },
  components: { NeufCases, ReglesMorpion, JoueursPoints },
  methods: {
    retourAccueil() {
      this.$emit('retourAccueil')
    },
    submit() { },
    score() { },
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
* {
  box-sizing: border-box;
}

h1 {
  margin: 0;
}

.padding {
  padding: 2vw;
}

.width {
  width: 100vw;
}

@media(min-width: 768px) {
  .spaceAround {
    display: flex;
    justify-content: space-around;
  }
}
</style>
