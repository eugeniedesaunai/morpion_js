<template>
    <article class="parent">
        <!-- revoir pour faire un for  :data-value=i -->
        <CaseMorpion v-for="i in 9" :key="i" :data-value='i' :joueurActuel='pion' @submit="chacunSonTour(i)"
            class="couleurBase">
        </CaseMorpion>

        <div v-if="joueurActuel.length == 0"> {{ premierJoueur }}</div>
        <div v-if="joueurActuel.length > 1"> {{ joueurSuivant }}</div>
    </article>
</template>

<script>
import CaseMorpion from './CaseMorpion.vue';
export default {
    name: "NeufCases",
    data() {
        return {
            tours: '',
            joueursSymbole: ['x', 'o'],
            pion: 'o',
            joueurActuel: "",
            combinaisonGagnante: [[1, 2, 3], [4, 5, 6], [7, 8, 9],
            [1, 4, 7], [2, 5, 8], [3, 6, 9], [1, 5, 9], [3, 5, 7]],
            valeurPremierJoueur: [],
            valeurDeuxiemeJoueur: [],
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
                this.pion = this.joueursSymbole[1]
                this.joueurActuel = this.joueurs[1]
                this.valeurDeuxiemeJoueur.push(numeroCase)
                console.log(this.pion, this.tours, this.joueurs[1], this.valeurDeuxiemeJoueur)

            }
            else {
                this.pion = this.joueursSymbole[0]
                this.joueurActuel = this.joueurs[0]
                this.valeurPremierJoueur.push(numeroCase)

                console.log(this.pion, this.tours, this.joueurs[0], this.valeurPremierJoueur)
            }
            this.tours++

            this.quiGagne()
        },

        //comparer le tableau des combinaisons gagnantes avec les tableaux joueurs 
        quiGagne() {

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
</style>
