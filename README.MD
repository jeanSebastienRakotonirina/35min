# Développer une interface de commande comme chez McDo

## Les écouteurs d'évènements (vers le composant)

Je dois vontacter mon comosant en amont, mon instance de vue; pour lui dire d'ajouter telle valeur, dans le tableau. Dans composant, je peux aussi défénir des méthodes qui appartiendront à fiche produit.

Composant :

            methods: {
                passer_commande: function(produit){
                    
                }

C'est une fonction qui prendra en paramètre le produit. Je vais lui dire d'émettre une fonction personnalisée.

Composant :

            methods: {
                passer_commande: function(produit){
                    this.$emit("commande_passee", produit)
                }
            }

En second paramètre, on fait passer le produit selectionner par l'évènement onclick.

html :

    <button v-on:click="passer_commande(nom)">Commander</button>

composant :

        Vue.component('fiche-produit', {
            template: `
            <div class="col-3">
                <p class='jumbotron'>
                    {{ nom }} <br />
                    <button v-on:click="commander(nom)">Commander</button>
                </p>
            </div>`
            ,
            props: ['nom'],
            methods: {
                passer_commande: function(produit){
                    this.$emit("commande_passee", produit)
                }
            }
        })

Maintenant, le tout est de revenir sur mon instance de vue et de déclencher ma fonction commander au moment où je reçois un évènement commande_passer :

Instance de vue :

        var app = new Vue({
            el: "#app",
            data: {
                user: "Bertrand",
                produits: ["Pizza", "Hamburger", "Cheeseburger", "Tacos"],
                commandes: [],
                affichage: "display-4"
            },
            methods: {
                commander: function(produit) {
                    this.commandes.push(produit)
                }
            }
        })

Comment faire ?