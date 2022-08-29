<template>
    <div class="texteCenter neon" @click="chacunSonTour"> {{ pion }}</div>
</template>

<script>
export default {

    name: 'CaseMorpion',
    data() {
        return {
            pion: ''
        }
    },
    props: {
        joueurActuel: String,
        resultat: String,
        finish: Boolean
    },

    methods: {
        chacunSonTour() {
            console.log(this.resultat);
            if (this.pion.length < 1 && this.finish == false) {
                this.pion = this.joueurActuel
                this.$emit('submit', this.pion);

            }
        }

    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
div {

    font-size: 4rem;
    color: #f07171;
    text-shadow: 0px 0px 10px #f07171;
}

@media(min-width: 768px) {
    .designBoutton {
        margin-left: 15rem;
        margin-right: 15rem;
        height: 6vh;
    }

    div {
        font-size: 5rem;
    }
}

@media(min-width: 1024px) {
    div {
        font-size: 6rem;
    }
}
</style>
