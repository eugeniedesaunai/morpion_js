<template>
    <article class="neufCases">
        <!-- revoir pour faire un for  :data-value=i -->
        <CaseMorpion v-for="i in 9" :key="i" :data-value='i' :joueurActuel='pion' :resultat='resultat' :finish='finish'
            @submit="chacunSonTour(i)" class="couleurBase">
        </CaseMorpion>
    </article>
    <article class="texteIndicatif alumi">
        <div v-if="joueurActuel.length == 0"> {{  premierJoueur  }} </div>
        <div v-else-if="joueurActuel.length > 1 && !finish"> {{  joueurSuivant  }}</div>
        <div v-if="resultat.length > 1"> {{  resultat  }}</div>
    </article>
    <article class="spaceAround ">
        <p class="indicateur indicateurJoueur texteCenter">{{  joueurs[0]  }}</p>
        <p class="indicateur indicateurPoint texteCenter">{{  scorePremierJoueur  }}</p>
        <p class="indicateur indicateurJoueur texteCenter">{{  joueurs[1]  }}</p>
        <p class="indicateur indicateurPoint texteCenter">{{  scoreDeuxiemeJoueur  }} </p>
    </article>
       <article> 
    <button> Rejouer</button>
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
            scoreDeuxiemeJoueur: 0,
            finish: false
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

        // fonction qui attribu aux joueurs un nombre paire ou impaire correspondant à un symbole, s'alternant au click
        // récupérer dans un tableau la data de chaques cases dés qu'un joueur clique sur une case
        chacunSonTour(numeroCase) {

            if ((this.tours % 2 == 1)) {
                this.pion = this.joueursSymbole[0]
                this.joueurActuel = this.joueurs[0]
                this.valeurDeuxiemeJoueur.push(numeroCase)
            }
            else {
                this.pion = this.joueursSymbole[1]
                this.joueurActuel = this.joueurs[1]
                this.valeurPremierJoueur.push(numeroCase)
            }
            this.tours++
            this.quiGagne()
        },
        //comparer le tableau des combinaisons gagnantes avec les tableaux joueurs en convertissant en string afin de 
        //pouvoir utiliser le include
        // changer la couleur des cases en cas de combinaison gagnante en sélectionant les cases et leurs rajoutants une classe
        quiGagne() {

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
                                cases[i].classList.add("grisClair");
                            }
                        }
                    }
                    this.resultat = this.joueurs[0] + " a gagné";
                    this.scorePremierJoueur++
                    this.finish = true
                }

                if (result2) {
                    let cases = document.querySelectorAll(".couleurBase")

                    for (let i = 0; i < cases.length; i++) {
                        for (let y = 0; y < tabCombinaison.length; y++) {

                            if (tabCombinaison[y] == cases[i].getAttribute("data-value")) {
                                cases[i].classList.add("grisFonce");
                            }
                        }
                    }
                    this.resultat = this.joueurs[1] + " a gagné";
                    this.scoreDeuxiemeJoueur++
                    this.finish = true
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
.texteIndicatif {
    color: #e5c7e2;
    padding-top: 1rem;
    padding-bottom: 0.6rem;
    text-shadow: 0px 0px 10px #f07171;
}

.couleurBase {
    background-color: #6a6869;
}

.couleurBase:hover {
    background-color: #ADACB5;
}

.grisClair {
    background-color: #444;
}

.grisFonce {
    background-color: #222;
}

.indicateur {
    box-shadow: -5px -5px 15px #444, 5px 5px 15px #222, inset 5px 5px 10px #444, inset -5px -5px 10px #222;
    color: #f07171;
    text-shadow: 0px 0px 10px #f07171;
    border-radius: 1.5rem;
    height: 6vh;
    display: flex;
    justify-content: center;
    align-items: center;
}


.indicateurJoueur {
    width: 25vw;
    padding: 1vw;

}

.indicateurPoint {
    width: 15vw;
    padding: 1vw;
}

.neufCases {
    width: 95vw;
    height: 50vh;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: repeat(3, 1fr);
    grid-column-gap: 2px;
    grid-row-gap: 2px;
}

@media(min-width: 768px) {
    .neufCases {
        width: 55vw;
        height: 55vh;
        margin-left: auto;
        margin-right: auto;
    }
}
</style>
