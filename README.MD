# Développer une interface de commande comme chez McDo

## L'écouteur d'évènement v-on 

html :

    <fiche-produit v-for="produit in produits" v-bind:nom="produit" v-on:commande-passee="commander"></fiche-produit>

v-on va lui dire de déclencher la fonction commander. Elle va être déclenché en cliquant et le produit que j'ai passé dans le composant émis va être récupérer par l'instance de vue.
