<template>
  <AccueilMorpion v-if="step == 1" />
  <ChoixJoueurs v-if="step == 2" @submit="majJoueurs" />
  <PremierMorpion v-if="step == 3" :joueurs="joueurs" />


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
  color: #2D3142;

}

.tailleMax {
  width: 100vw;
  height: 100vh;
}

.flexColumn {
  display: flex;
  flex-direction: column;
}

body {
  background-color: #F2F4F3;
  width: 100vw;
  height: 100vh;
  margin: 0;
}

.designBoutton {
  background-color: #2D3142;
  color: #D8D5DB;
  border-radius: 1.5rem;
  margin-left: 6rem;
  margin-right: 6rem;
  height: 4vh;
}

@media(min-width: 768px) {
  .designButton {
    margin-left: 15rem;
    margin-right: 15rem;
    height: 6vh;
  }
}

@media(min-width: 1024px) {
  .designButton {
    margin-left: 28rem;
    margin-right: 28rem;
    height: 8vh;
  }
}
</style>
