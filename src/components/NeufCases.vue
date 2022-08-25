<template>
    <article class="parent">
        <!-- revoir pour faire un for  -->
        <CaseMorpion @click="chacunSonTour" :joueurActuel='pion' class="div1"></CaseMorpion>
        <CaseMorpion @click="chacunSonTour" :joueurActuel='pion' class="div2"></CaseMorpion>
        <CaseMorpion @click="chacunSonTour" :joueurActuel='pion' class="div3"></CaseMorpion>
        <CaseMorpion @click="chacunSonTour" :joueurActuel='pion' class="div4"></CaseMorpion>
        <CaseMorpion @click="chacunSonTour" :joueurActuel='pion' class="div5"></CaseMorpion>
        <CaseMorpion @click="chacunSonTour" :joueurActuel='pion' class="div6"></CaseMorpion>
        <CaseMorpion @click="chacunSonTour" :joueurActuel='pion' class="div7"></CaseMorpion>
        <CaseMorpion @click="chacunSonTour" :joueurActuel='pion' class="div8"></CaseMorpion>
        <CaseMorpion @click="chacunSonTour" :joueurActuel='pion' class="div9"></CaseMorpion>
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
            combinaisonGagnante: [[1, 2, 3], [4, 5, 6], [7, 8, 9], [1, 4, 7], [2, 5, 8], [3, 6, 9], [1, 5, 9], [3, 5, 7]]
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


.div1 {
    background-color: #ADACB5;
    grid-area: 1 / 1 / 2 / 2;
}

.div1:hover {
    background-color: #EAE8FF;
}

.div2 {
    background-color: #EAE8FF;
    grid-area: 1 / 2 / 2 / 3;
}

.div2:hover {
    background-color: #ADACB5;
}

.div3 {
    background-color: #ADACB5;
    grid-area: 1 / 3 / 2 / 4;
}

.div3:hover {
    background-color: #EAE8FF;
}

.div4 {
    background-color: #EAE8FF;
    grid-area: 2 / 1 / 3 / 2;
}

.div4:hover {
    background-color: #ADACB5;
}

.div5 {

    background-color: #ADACB5;
    grid-area: 2 / 2 / 3 / 3;
}

.div5:hover {
    background-color: #EAE8FF;
}

.div6 {
    background-color: #EAE8FF;
    grid-area: 2 / 3 / 3 / 4;
}

.div6:hover {
    background-color: #ADACB5;
}

.div7 {
    background-color: #ADACB5;
    grid-area: 3 / 1 / 4 / 2;
}

.div7:hover {
    background-color: #EAE8FF;
}

.div8 {
    background-color: #EAE8FF;
    grid-area: 3 / 2 / 4 / 3;
}

.div8:hover {
    background-color: #ADACB5;
}

.div9 {
    background-color: #ADACB5;
    grid-area: 3 / 3 / 4 / 4;
}

.div9:hover {
    background-color: #EAE8FF;
}

@media(min-width: 768px) {
    .parent {
        height: 70vh;
    }
}
</style>
<!-- 123
456
789
147
258
369
159
357 -->