<template>
    <div @click="chacunSonTour"> {{ pion }}</div>
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
            }
        }

    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
