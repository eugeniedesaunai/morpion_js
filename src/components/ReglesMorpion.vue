<template>
    <article>
        <h2 class="texteCenter ">Règles</h2>
        <ol class="spaceAround flexColumn paddingRegles">
            <li>Jeu qui se joue à deux joueurs, sur un damier de 3 cases par 3 cases.</li>
            <li>Chaque joueur est représenté par un "symbole"</li>
            <li>Un joueur utilise toujours le même type de "symbole"</li>
            <li>Un premier joueur dessine son symbole sur une case. Puis c'est au tour de l'autre joueur de dessiner son
                symbole sur une case vide.</li>
            <li>Le but du jeu est de réussir à aligner ses trois symboles (horizontal, vertical ou diagonale), on
                remporte
                alors la partie.</li>
            <li>Si la grille est remplie et qu'aucune ligne ne comporte trois symboles identiques, les joueurs finissent
                par
                un match nul.</li>
        </ol>
    </article>
</template>

<script>
export default {
    name: 'ReglesMorpion',
    props: {

    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@media(min-width: 768px) {
    .paddingRegles {
        padding: 3rem;
    }
}
</style>
