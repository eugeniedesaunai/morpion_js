<template>
  <AccueilMorpion v-if="step == 1" />
  <PremierMorpion v-if="step == 3" :joueurs="joueurs" />
  <ChoixJoueurs v-else @submit="majJoueurs" />

</template>

<script>
import AccueilMorpion from './components/AccueilMorpion.vue';
import PremierMorpion from './components/PremierMorpion.vue';
import ChoixJoueurs from './components/ChoixJoueurs.vue';

export default {
  name: 'App',
  data() {
    return {
      step: 2,
      joueurs: []
    }
  },
  components: {
    AccueilMorpion,
    PremierMorpion,
    ChoixJoueurs
  },
  methods: {
    majJoueurs(nomJoueur) {
      this.joueurs.push(nomJoueur)
      console.log(this.joueurs)
      if (this.joueurs.length == 2) this.step++
    }
  },

}
</script>

<style>
.texteCenter {
  text-align: center;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;

}

.flexColumn {
  display: flex;
  flex-direction: column;
}

body {
  width: 100vw;
  height: 100vh;
  margin: 0;
}
</style>
