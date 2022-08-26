<template>
    <div class="texteCenter" @click="chacunSonTour"> {{ pion }}</div>
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
    },

    methods: {
        chacunSonTour() {
            if (this.pion.length < 1) {
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
}

@media(min-width: 768px) {
    .designBoutton {
        margin-left: 15rem;
        margin-right: 15rem;
        height: 6vh;
    }
}

@media(min-width: 1024px) {
    div {
        font-size: 8rem;
    }
}
</style>
