# Stage_MountainCar

Le but de ce jeu est de faire en sorte que la voiture monte la colline de droite pour atteindre le drapeau. 
Problème : la voiture n'a pas assez de puissance pour monter la colline. 
-> La voiture doit apprendre qu'elle doit monter une colline pendant un certain temps, 
puis accélérer pour descendre la colline et remonter de l'autre côté, et répéter jusqu'à ce qu'elle ait suffisamment d'élan pour atteindre le sommet de la colline.

## Nous avons 3 classes + le main
Classe Model : Cette classe contient les opérations TensorFlow et les définitions du modèle
Classe memory : Cette classe est celle où la mémoire des actions, des récompenses et des états est stockée et récupérée
Classe GameRunner : Cette classe est la principale classe de formation et de contrôle des agents

### Classe model:

Nous avons l'initialisation de nos variable donc les etats et les actions possibles. 
Ensuite on appelle la methode qui va definir la structure du modele.

On a donc la methode _define_model qui initialise les placeholder et les layers
Le rôle des placeholder: ils contiennent les données d'entrée afin qu'elles soit traitées correctement.
Pour tf2 : Les placeholder ne sont plus dans tf2, comme alternative nous utiliserons la librairie Keras.
Ensuite nous avons les layers, qui sont les couches d'opération (50 ici) sur nos données.
Pour tf2: Comme les placeholder, nous utiliserons la librairie Keras afin de s'occuper des layers.

Les methodes predict renvoie la sortie du reseau. predict_one fonctionne avec un seul état et predict_batch avec tout les états.
La methode train_batch sert à faire l'entrainement du reseau avec tout les états.

### Classe Memory:

Cette classe va stocker tout nos resultats afin de pouvoir les traiter.

### Classe GameRunner:

C'est la classe qui va definir toutes les regles de notre jeu et comment on doit se comporter.
On va utiliser la librairie 'gym' afin de créer une fenetre animé qui va simuler notre montagne et notre voiture en mouvement.
Lorsque la voiture à reussi, on enregistre tout avec la classe memory et cela va permettre d'améliorer notre IA.

Enfin la classe main instancie notre jeu et lance la simulation.


## Pour tensorflow 2:

Pour réaliser la transition vers TF2, nous devons voir ce qui n'est plus à jour. On remarque rapidement que les placeholder et les layers ne s'instancie plus comme avant.
Pour cela, nous devons utiliser la librairie 'Keras' et remplacer tout les anciens appels de layers avec : tf.keras.layers.layerName
Pour les placeholder, nous pouvons aussi utiliser Keras et remplacer par 'tf.keras.Input' mais cela implique de definir après la forme des entrées.




