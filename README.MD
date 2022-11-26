# Développer une interface de commande comme chez McDo

## Les composants

html :

            <h1 v-bind:class="affichage">Produits disponibles</h1>
            <div class="row">
                <div class="col-3" v-for="produit in produits">
                    <p class="jumbotron">
                        {{ produit }} <br>
                        <button v-on:click="commander(produit)">Commander</button>
                    </p>
                </div>
            </div>

On va remplacer tout ça par une simple balise sur mesure.

html :

    <fiche-produit></fiche-produit>

Au dessu de var app=({}), on place la déclaration de notre composant :

script :

        Vue.component('fiche-produit', {
            
        })

En premier paramètre le nom du composant et en deuxième paramètre un objet javascript. La première propriété qu'on peut lui passer s'appelle template. Elle prendra une chaine de caractère en paramètre qui va définir l'affichage en html de notre composant.

L'idée est de recevoir des balises html sous forme de propriétés. Dans le composant, créer une méthode props (propriétés) que l'application va être amené à recevoir, seront simplement listés dans un tableau.

Html: 

    <fiche-produit v-for="produit in produits" v-bind:nom="produit"></fiche-produit>

On va bindé sa proporiété nom au produit, on fait boucler chaque produit dans une variable produit et à chaque fois, on va associer le nom au produit passer en paramètre.

script :

            template: `
            <p class='jumbotron'>
                {{ nom }}
            </p>`,
            props: ['nom']

Cela me permet de l'afficher comme une propriété data.