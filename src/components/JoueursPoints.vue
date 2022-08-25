<template>
    <section class="spaceAround ">
        <p class="color indicateurJoueur texteCenter">{{ joueurs[0] }}</p>
        <p class="color indicateurPoint texteCenter">point joueur 1</p>
        <p class="color indicateurJoueur texteCenter">{{ joueurs[1] }}</p>
        <p class="color indicateurPoint texteCenter">point joueur 2</p>
        <p class="color indicateurJoueur texteCenter"> Retour Menu</p>
    </section>
</template>

<script>
export default {
    name: 'JoueursPoints',
    props: {
        joueurs: Array
    },
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
