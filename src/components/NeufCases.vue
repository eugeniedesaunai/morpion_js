<template>
    <article class="parent">
        <!-- revoir pour faire un for  :data-value=i -->
        <CaseMorpion v-for="i in 9" :key="i" :data-value='i' :joueurActuel='pion' :resultat="resultat" @click="score"
            @submit="chacunSonTour(i)" class="couleurBase">
        </CaseMorpion>
        <div>{{ scorePremierJoueur }}</div>
        <div v-if="joueurActuel.length == 0"> {{ premierJoueur }} </div>
        <div v-if="joueurActuel.length > 1"> {{ joueurSuivant }}</div>
    </article>
</template>

<script>
import CaseMorpion from './CaseMorpion.vue';
export default {
    name: "NeufCases",
    data() {
        return {
            tours: 0,
            joueursSymbole: ['x', 'o'],
            pion: 'x',
            joueurActuel: "",
            combinaisonGagnante: [[1, 2, 3], [4, 5, 6], [7, 8, 9],
            [1, 4, 7], [2, 5, 8], [3, 6, 9], [1, 5, 9], [3, 5, 7]],
            valeurPremierJoueur: [],
            valeurDeuxiemeJoueur: [],
            resultat: "",
            scorePremierJoueur: 0,
            scoreDeuxiemeJoueur: 0

        }
    },
    props: {
        joueurs: Array,

    },
    computed: {
        premierJoueur() {
            return this.joueurs[0] + " commence"
        },
        joueurSuivant() {
            return "A ton tour " + this.joueurActuel
        }

    },
    methods: {
        score() {
            this.$emit('score', this.scorePremierJoueur)
            this.$emit('score', this.scoreDeuxiemeJoueur)
        },
        // fonction qui attribu aux joueurs un nombre paire ou impaire correspondant à un symbole, s'alternant au click
        // récupérer dans un tableau la data de chaques cases dés qu'un joueur clique sur une case
        chacunSonTour(numeroCase) {

            if ((this.tours % 2 == 1)) {
                this.pion = this.joueursSymbole[0]
                this.joueurActuel = this.joueurs[0]
                this.valeurDeuxiemeJoueur.push(numeroCase)
                console.log(this.pion, this.tours, this.joueurs[1], this.valeurDeuxiemeJoueur)

            }
            else {
                this.pion = this.joueursSymbole[1]
                this.joueurActuel = this.joueurs[1]
                this.valeurPremierJoueur.push(numeroCase)
                console.log(this.pion, this.tours, this.joueurs[0], this.valeurPremierJoueur)
            }
            this.tours++
            this.quiGagne()
        },
        //comparer le tableau des combinaisons gagnantes avec les tableaux joueurs en convertissant en string afin de 
        //pouvoir utiliser le include
        // changer la couleur des cases en cas de combinaison gagnante
        quiGagne() {
            /*           if (this.valeurPremierJoueur.includes(1)) {
                          if (this.valeurPremierJoueur.includes(2)) {
                              if (this.valeurPremierJoueur.includes(3)) {
                                  this.valeurPremierJoueur = this.joueurs[0]
                                  this.scorePremierJoueur++
                                  console.log(this.joueurs[0] + " a gagné", this.scorePremierJoueur)
                              }
                          }
                      }
                      if (this.valeurDeuxiemeJoueur.includes(1)) {
                          if (this.valeurDeuxiemeJoueur.includes(2)) {
                              if (this.valeurDeuxiemeJoueur.includes(3)) {
                                  this.valeurDeuxiemeJoueur = this.joueurs[1]
                                  this.scoreDeuxiemeJoueur++
                                  console.log(this.joueurs[1] + " a gagné", this.scoreDeuxiemeJoueur)
                              }
                          }
                      } */

            this.combinaisonGagnante.forEach(tabCombinaison => {
                let joueur1String = this.valeurPremierJoueur.join(" ");
                let joueur2String = this.valeurDeuxiemeJoueur.join(" ");

                let result1 = tabCombinaison.every(combinaison => joueur1String.includes(combinaison));
                let result2 = tabCombinaison.every(combinaison => joueur2String.includes(combinaison));


                if (result1) {
                    let cases = document.querySelectorAll(".couleurBase")

                    for (let i = 0; i < cases.length; i++) {
                        for (let y = 0; y < tabCombinaison.length; y++) {

                            if (tabCombinaison[y] == cases[i].getAttribute("data-value")) {
                                cases[i].classList.add("black");
                            }
                        }
                    }
                    this.resultat = "joueur 1 a gagné";
                    this.scorePremierJoueur++
                }
                if (result2) {
                    let cases = document.querySelectorAll(".couleurBase")

                    for (let i = 0; i < cases.length; i++) {
                        for (let y = 0; y < tabCombinaison.length; y++) {

                            if (tabCombinaison[y] == cases[i].getAttribute("data-value")) {
                                cases[i].classList.add("red");
                            }
                        }
                    }
                    this.resultat = "joueur 2 a gagné";
                    this.scoreDeuxiemeJoueur++
                }

            })
        },
    },

    components: {
        CaseMorpion,
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.parent {
    width: 95vw;
    height: 50vh;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: repeat(3, 1fr);
    grid-column-gap: 2px;
    grid-row-gap: 2px;
}

.couleurBase {
    background-color: #ADACB5;
}

.couleurBase:hover {
    background-color: #EAE8FF
}

@media(min-width: 768px) {
    .parent {
        height: 70vh;
    }
}

.black {
    background-color: black;
}

.red {
    background-color: red;
}
</style>
