<template>
    <section class="texteCenter flexColumn">
        <article class="flexColumn alumi">
            <label for="premierJoueur">Nom du premier joueur : {{  premierJoueur  }}</label>
            <input class="marginText designBoutton texteCenter" type="text" name="" id="premierJoueur"
                v-model="premierJoueur">
        </article>
        <article class="flexColumn alumi">
            <label for="deuxiemeJoueur ">Nom du deuxième joueur : {{  deuxiemeJoueur  }}</label>
            <input class="marginText designBoutton texteCenter" type="text" name="" id="deuxiemeJoueur"
                v-model="deuxiemeJoueur">
        </article>
        <input class="designBoutton" type="submit" value="Prêt" @click="submit">
        <div class="popUpJoueur hidden"> Veuillez indiquer le nom des deux joueurs</div>
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
            if (this.premierJoueur.length > 0 && this.deuxiemeJoueur.length > 0) {
            this.$emit('submit', this.premierJoueur);
            this.$emit('submit', this.deuxiemeJoueur);
            }
            else{
            let popUpJoueur = document.querySelector('.popUpJoueur');
            popUpJoueur.classList.remove("hidden");
/*             setTimeout(() => {
                popUpJoueur.classList.add("hidden");
            }, 10000); */
      }
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
    color: #f07171;
    text-shadow: 0px 0px 10px #f07171;
}

.marginSubmit {
    margin-left: 5em;
    margin-right: 5em;
}

.popUpJoueur{
    position: absolute;
    background-color: #f07171;
    color: #6a6869;
    width: 50%;
    height: auto;
    top: 2%;
    left: 2%;
    border-radius: 2rem;
    font-size: 1rem;
    padding:1rem;
}

@media(min-width: 768px) {
    .marginText {
        margin: 2em;
        margin-left: 9em;
        margin-right: 9em;
    }

    .popUpJoueur{
         width: 40%;
font-size: 1.5rem;
    }
}

@media(min-width: 1024px) {
    .marginText {
        margin: 2em;
        margin-left: 10em;
        margin-right: 10em;
    }

    .popUpJoueur{
         width: 30%;
font-size: 1.5rem;
    }
}
</style>