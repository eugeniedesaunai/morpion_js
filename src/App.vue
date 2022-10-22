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
      step: 1,
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

    },
    jouer() {
      this.step++
    },
    jeuAccueil() {
      this.step = this.step - 2
    }
  },

}
</script>

<style>
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

@import url('https://fonts.googleapis.com/css2?family=Neonderthaw&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Alumni+Sans+Pinstripe&display=swap');

.neon {
  font-family: 'Neonderthaw', cursive;

}

.alumi {
  font-family: 'Alumni Sans Pinstripe', sans-serif;

}

#app {
  font-family: 'Alumni Sans Pinstripe', sans-serif;
  color: #e5c7e2;
  font-size: 2rem;
  cursor: url(./img/cursor1.png), pointer;
}

/* menu */

.bm-burger-bars {
  background-color: #444;
}

.bm-cross {
  background: #444;
}

.cross-style {
  cursor: url(./img/cursor1.png), pointer;
}

.bm-burger-button {
  cursor: url(./img/cursor1.png), pointer;
}

.bm-overlay {
  background: #222;
  ;
}


.texteCenter {
  text-align: center;
}

.flexColumn {
  display: flex;
  flex-direction: column;
}

.tailleMax {
  width: 100vw;
  height: 100vh;
}

.spaceAround {
  display: flex;
  justify-content: space-around;
}

.wrap {
  display: flex;
  flex-wrap: wrap;
}

.hidden{
  visibility: hidden;
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
  text-transform: uppercase;
  font-size: 2rem;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 1.5rem;
  margin-left: 6rem;
  margin-right: 6rem;
  height: 6vh;
  cursor: url(./img/cursor1.png), pointer;

  background: #333;
  border: none;
  box-shadow: -5px -5px 15px #444, 5px 5px 15px #222, inset 5px 5px 10px #444, inset -5px -5px 10px #222;
  color: #222;
}

.designBoutton:hover {
  box-shadow: -5px -5px 15px #444, 5px 5px 15px #222, inset 5px 5px 10px #222, inset -5px -5px 10px #444;
  font-size: 1.8rem;
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
    height: 7vh;
  }
}

@media(min-width: 1024px) {
  .designBoutton {
    margin-left: 20rem;
    margin-right: 20rem;
    margin-top: 1rem;
    height: 7vh;
  }
}
</style>
