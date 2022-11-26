# Développer une interface de commande comme chez McDo

1. On démarre avec un fichier index Html 

2. Intégrer, Installer Vue js :

Dans la documentation fr.vuejs.org, aller dans "Essentiel>>Installation".
Plusieurs façons, intégration du fichier directement, ou utilisation du CDN, ligne de commande, etc...

Par contre 2 versions de vue : 

- Développement qui va permettre de montrer des avertissements, des erreurs qui seraient masqués en version production

- Production est minifiée, elle sera plus rapide, plus légère

On va utiliser le CDN pour intégrer directement Vuejs et on va utiliser la version de prototypage :

<head>

...

<script src="https://cdn.jsdelivr.net/npm/vue@2.7.8/dist/vue.js"></script>

<!-- CDN de Bootstrap pour simplement designer notre appli-->

<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.6.2/dist/css/bootstrap.min.css" integrity="sha384-xOolHFLEh07PJGoPkLv1IbcEPTNtaed2xpHsD9ESMhqIYd0nLMwNLD69Npy4HI+N" crossorigin="anonymous">

</head>

Pour implémenter VueJS, il va travailler en synergie avec une balise html ici #app, qui contiendra à chaque fois l'instance de Vue. Viser une balise en particulier, qui contiendra toutes les autres, une balise racine. id app est une convention.

A l'intérieur de cette balise, je vais faire opérer VueJS.

3. Créer une instance de vue

Dans une balise script, on crée une nouvelle instance, dans laquelle on fait passer un objet contenant des paramètre, le premier étant el, pour dire qu'on va viser la balise ayant pour id app :

    <script>
        var app = new Vue({
            el:"#app"
        })
    </script>

A partir de là, Vue est initialisé sur toute mon application. Le code contenu dans app va avoir une liaison directe avec l'interface. On va pouvoir changer une valeur qui serait présente à l'intérieur du script et ça changerait en temps réel sur l'interface, très rapide à implémenter.

4. Les données (l'état)

Elles vont être contenu dans une autre clé de mon objet javascript qui est la propriété data. Data va reprendre un autre objet javascript, je vais pouvoir entrer toutes les données que je veux. Toutes ces données s'appellent l'état.

Coder en dur, on a un utilisateur user qui contient le string Bertrand. Pour afficher cette donnée ou état dans la balise id app, on va faire du rendu déclaratif entre 2 accolades ouvrantes et fermantes.

{{ user }}

Ainsi, je peux voir le contenu de ma variable interpolé directement. Je peux modifier ça en temps réel dans ma console javascript de mon navigateur. En tapant app.user="Jean-Sébastien" va remplacer la valeur Bertrand en temps réel. On va pouvoir modifier les données de l'interface de façon réactive en temps réel.