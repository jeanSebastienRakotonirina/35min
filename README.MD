# Développer une interface de commande comme chez McDo

## Transmettre des infos du html vers la partie script = data-binding

On va permettre à l'utilisateur de rentrer son nom. Je voudrais que mon user s"adapte à mon input et non plus l'inverse.

VueJS met à disposition des directives, des nouveaux attributs que VueJS va implémenter dans le html et qui vont permettre d'adopter des comportements réactifs.

1. La directive V-model

L'attribut v-model synchronise le contenu de l'input avec quelque chose qui est dans mon état, dans le script.

    v-model = "user"

Quand je recharge la page, elle affiche la valeur par défaut "Bertrand", parce que c'est la valeur définit dans mon user. Et quand je modifie la valeur dans l'input, il va faire un affichage en temps réel.

Maintenant, on va créer une liste de produits.

    produits: ["Pizza", "Hamburger", "Cheeseburger", "Tacos"]

J'aimerais bien les répercuter dans mon interface.

2. La directive V-for 

Elle sert à énumérer une liste. L'idée est de créer un carré pour chaque produit avec le nom correspond au produit dedans.

    <div class="col-3" v-for="produit in produits">

Cela va répéter la balise et son contenu en fonction du nombre de produits dans le tableau et pour chacune de ses répétitions, on va avoir le contenu du tableau qui sera dans la variable produit.

L'idée est de pouvoir cliquer sur un produit et le renvoie dans une liste de produits dans un panier, produit que j'ai commandé.

On crée un tableau de commandes vide, qu'on remplira en cliquant sur l'élément produit correspondant.

Pour ça, mon instance de vue va pouvoir comporter une autre méthode.

3. Les méthodes

On crée une méthode "commander" qui correspond à une function.

Côté script :

    methods: {
        commander: function(produit) {
            this.commandes.push(produit)
        }
    }

Côté Html :

    <div class="col-3" v-for="produit in produits">

et

    <button v-on:click="commander(produit)">Commander</button>


Pour faire passer les produits, soit on utilise l'index, soit le produit en string.

4. Afficher la liste des commandes

Html :

    <h1 class="display-4">Produits commandés</h1>
    <ul>
        <li v-for="commande in commandes">{{ commande }}</li>   
    </ul>

La liste se remplit, l'interface est dynamique. Faire un meilleur rendu, car il n'y a pas encore de produits commandés. Le titre s"affiche quand même.

5. La directive conditionnelle v-if

html :

    <h1 class="display-4" v-if="false">Produits commandés</h1>

Je peux ainsi mettre une condition sur l'affichage, si je mets false, le titre ne s'affiche pas.

html :

    <h1 class="display-4" v-if="commandes.length > 0">Produits commandés</h1>

Maintenant je n'affiche le titre que si la longueur du tableau de commandes est supérieur à 0, autrement dit, si le tableau de commandes comporte un produit au moins.

Maintenant, si je veux faire varier des attributs html, par exemple des classes disponibles, comment faire dans VueJS ?

6. La directive v-bind

Je vais pouvoir relier une classe par exemple, display-4, à une valeur dans mes données.

Par exemple, une variable affichage que je vais aller définir 

Dans html :

    <h1 v-bind:class="affichage">Produits disponibles</h1>

Dans data :

    affichage: "display-4"

Les produits disponibles sont bindés à la variable affichage définis dans data, par contre je peux venir la modifier "display-1". Il est possible de faire varier tout l'affichage directement.

On peut constater dans l'application 2 blocs de codes relativement similaires, même si ils ne sont pas codés de la même façon : 

- Celui pour afficher les commandes
- Et l'autre pour afficher les produits disponibles

On aurait envie de remettre tout ça dans une même forme et de pouvoir réutiliser le code.

