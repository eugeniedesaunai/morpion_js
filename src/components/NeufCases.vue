<template>
    <article class="parent">
        <!-- revoir pour faire un for  -->
        <CaseMorpion v-for="i in 9" :key=i :data-value=i @click="chacunSonTour" :joueurActuel='pion'
            class=" div1 couleurBase">
        </CaseMorpion>
        <CaseMorpion @click="chacunSonTour" :joueurActuel='pion' class="div2 couleurBase"></CaseMorpion>
        <CaseMorpion @click="chacunSonTour" :joueurActuel='pion' class="div3 couleurBase"></CaseMorpion>
        <CaseMorpion @click="chacunSonTour" :joueurActuel='pion' class="div4 couleurBase"></CaseMorpion>
        <CaseMorpion @click="chacunSonTour" :joueurActuel='pion' class="div5 couleurBase"></CaseMorpion>
        <CaseMorpion @click="chacunSonTour" :joueurActuel='pion' class="div6 couleurBase"></CaseMorpion>
        <CaseMorpion @click="chacunSonTour" :joueurActuel='pion' class="div7 couleurBase"></CaseMorpion>
        <CaseMorpion @click="chacunSonTour" :joueurActuel='pion' class="div8 couleurBase"></CaseMorpion>
        <CaseMorpion @click="chacunSonTour" :joueurActuel='pion' class="div9 couleurBase"></CaseMorpion>
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
            pion: 'x',
            joueurActuel: "",
            combinaisonGagnante: [123, 456, 789, 147, 258, 369, 159, 357]
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
        chacunSonTour() {
            if ((this.tours % 2 == 1)) {
                this.pion = this.joueursSymbole[0]
                this.joueurActuel = this.joueurs[0]
                this.tours++
                console.log(this.pion, this.tours, this.joueurs[0])
            }
            else {
                this.pion = this.joueursSymbole[1]
                this.joueurActuel = this.joueurs[1]
                this.tours++
                console.log(this.pion, this.tours, this.joueurs[1])
            }
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

.div1 {
    grid-area: 1 / 1 / 2 / 2;
}

.div2 {
    grid-area: 1 / 2 / 2 / 3;
}

.div3 {
    grid-area: 1 / 3 / 2 / 4;
}

.div4 {
    grid-area: 2 / 1 / 3 / 2;
}

.div5 {
    grid-area: 2 / 2 / 3 / 3;
}

.div6 {
    grid-area: 2 / 3 / 3 / 4;
}

.div7 {
    grid-area: 3 / 1 / 4 / 2;
}

.div8 {
    grid-area: 3 / 2 / 4 / 3;
}

.div9 {
    grid-area: 3 / 3 / 4 / 4;
}

@media(min-width: 768px) {
    .parent {
        height: 70vh;
    }
}
</style>
