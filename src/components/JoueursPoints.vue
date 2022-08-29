<template>
    <section class="spaceAround ">
        <p class="color indicateurJoueur texteCenter">{{ joueurs[0] }}</p>
        <p class="color indicateurPoint texteCenter">{{ scorePremierJoueur }}</p>
        <p class="color indicateurJoueur texteCenter">{{ joueurs[1] }}</p>
        <p class="color indicateurPoint texteCenter"> {{ scoreDeuxiemeJoueur }}</p>
        <input class=" designBoutton indicateurJoueur texteCenter" type="button" value="Retour Accueil">
    </section>
</template>

<script>
export default {
    name: 'JoueursPoints',
    props: {
        joueurs: Array,
        scorePremierJoueur: Number,
        scoreDeuxiemeJoueur: Number
    },
    methods: {

    }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.color {
    background-color: #2D3142;
    color: #D8D5DB;
    border-radius: 1.5rem;
}

.indicateurJoueur {
    width: 20vw;
    padding: 1vw;
}

.indicateurPoint {
    width: 10vw;
    padding: 1vw;
}
</style>
