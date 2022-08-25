<template>
    <section class="texteCenter">
        <article class="flexColumn">
            <label for="premierJoueur">Nom du Joueur 1 : {{ premierJoueur }}</label>
            <input class="marginText" type="text" name="" id="premierJoueur" v-model="premierJoueur">
        </article>
        <article class="flexColumn">
            <label for="deuxiemeJoueur">Nom du Joueur 2 : {{ deuxiemeJoueur }}</label>
            <input class="marginText" type="text" name="" id="deuxiemeJoueur" v-model="deuxiemeJoueur">
        </article>
        <p> </p>
        <input class="marginSubmit" type="submit" value="Prêt" v-if="joueursPret" @click="submit">
    </section>
</template>

<script>
export default {
    name: "ChoixJoueurs",
    data() {
        return {
            premierJoueur: "",
            deuxiemeJoueur: "",
        }
    },
    computed: {
        joueursPret() {
            return this.premierJoueur.length > 0 && this.deuxiemeJoueur.length > 0
        },
    },
    methods: {
        submit() {
            this.$emit('submit', this.premierJoueur);
            this.$emit('submit', this.deuxiemeJoueur);
        }
    },
}
</script>

<style scoped>
section {
    height: 100vh;
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
}

.marginText {
    margin: 2em;
}

.marginSubmit {
    margin-left: 5em;
    margin-right: 5em;
}

@media(min-width: 768px) {
    .marginText {
        margin: 2em;
        margin-left: 9em;
        margin-right: 9em;
    }

    .marginSubmit {
        margin-left: 20em;
        margin-right: 20em;
    }
}

@media(min-width: 1024px) {
    .marginText {
        margin: 2em;
        margin-left: 15em;
        margin-right: 15em;
    }

    .marginSubmit {
        margin-left: 25em;
        margin-right: 25em;
    }
}
</style>