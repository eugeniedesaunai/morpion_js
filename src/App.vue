<template>
  <AccueilMorpion v-if="step == 1" @morpion="jouer" />
  <ChoixJoueurs v-if="step == 2" @submit="majJoueurs" />
  <PremierMorpion v-if="step == 3" :joueurs="joueurs" @retourAccueil="jeuAccueil" />


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
    ChoixJoueurs,
  },
  methods: {
    majJoueurs(nomJoueur) {
      this.joueurs.push(nomJoueur)
      if (this.joueurs.length == 2) this.step++
      console.log(this.step)
    },
    jouer() {
      this.step++
      console.log(this.step)
    },
    jeuAccueil() {
      this.step = this.step - 2
      console.log(this.step)
    }
  },

}
</script>

<style>
.texteCenter {
  text-align: center;
}

.tailleMax {
  width: 100vw;
  height: 100vh;
}

.flexColumn {
  display: flex;
  flex-direction: column;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  width: 100vw;
  height: 100vh;
  margin: 0;
  background: #333;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #ddd3e1;
}

/*  bouton */


.noselect {
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  -webkit-tap-highlight-color: transparent;
}

.designBoutton {
  border-radius: 1.5rem;
  margin-left: 6rem;
  margin-right: 6rem;
  height: 4vh;
  cursor: url('./img/morpion.png'), pointer;
  background: #333;
  border: none;
  box-shadow: -5px -5px 15px #444, 5px 5px 15px #222, inset 5px 5px 10px #444, inset -5px -5px 10px #222;
  color: #222;
  font-size: 16px;
}

.designBoutton:hover {
  box-shadow: -5px -5px 15px #444, 5px 5px 15px #222, inset 5px 5px 10px #222, inset -5px -5px 10px #444;
  font-size: 15px;
  transition: 500ms;
}

.designBoutton:focus {
  outline: none;
}

.designBoutton:hover {
  color: #f07171;
  text-shadow: 0px 0px 10px #f07171;
}


@media(min-width: 768px) {
  .designBoutton {
    margin-left: 15rem;
    margin-right: 15rem;
    height: 6vh;
  }
}

@media(min-width: 1024px) {
  .designBoutton {
    margin-left: 28rem;
    margin-right: 28rem;
    height: 8vh;
  }
}
</style>
