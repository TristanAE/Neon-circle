# Neon-circle
Ruban de LEDS programmables sous la forme d’un cercle fixé au mur et contrôlable par infrarouge.


# I-	Conception du ruban LED

Pour fabriquer un cercle en néon, il nous faut acheter un ruban de LEDS programmes individuellement ainsi qu’un tube flexible transparent pour y insérer notre banderole. 
L’épaisseur de la fente du tube doit être légèrement supérieur à quelques millimètres de celle du ruban LED pour pouvoir le faire glisser à l’intérieur plus facilement.
Une fois les deux éléments mis ensemble, il nous faut coller les deux extrémités du tube l’un à l’autre pour former un cercle, en veillant à bien laisser ressortir les fils du ruban pour les brancher à l’Arduino Nano.



# II-	Conception électronique et informatique

  a)	Branchement des LEDS et du capteur infrarouge

Pour pouvoir contrôler l’allumage des LEDS du ruban, on connecte les 3 fils à la carte Arduino Nano : au Ground, 5V et à un pin digital.
Pour le capteur infrarouge, on le branche également au Ground et au 5V puis à un autre pin digital disponible.

b)	Programmation des LEDS et du capteur infrarouge

Notre code se fera sous l’IDE Arduino et deux bibliothèques nous serons nécessaires :
•	FastLED pour le contrôle des LEDS individuellement 
•	IrRemote pour le contrôle du module infrarouge

Allumage des LEDS :

Après avoir déclaré les variables du projet ( comme le nombre de LEDS du ruban et la référence) et mis en route les différentes bibliothèques dans le setup, nous déclarons deux fonctions qui seront nos deux types d’allumage différents du ruban : 
•	Un allumage des LEDS une par une en bleu pour avoir l’effet d’un fluide
•	Un allumage des LEDS progressif en blanc pour avoir l’effet d’un chargement

Dans le loop du programme nous mettons en place deux conditions qui appellerons l’une de nos deux fonctions en fonction du bouton pressé par la télécommande.
Le code pour allumer les lumières est grandement simplifié avec la bibliothèque car il nous suffit d’utiliser une boucle for, et à l’intérieur, donner les instructions d’allumage pour chacune d’entre elle.
Dans notre premier mode : lorsqu’une LED s’allume en bleu, la précédente s’étend.
Dans notre deuxième mode : Toutes les LEDS s’allument en blanc progressivement à une certaine vitesse puis arrivées au bout, s’éteignent également progressivement mais plus rapidement.
Les fonctions doivent se répéter à l’infini sous l’effet d’une boucle while. 

Contrôle par infrarouge :

Le choix du type d’allumage se fait par infrarouge. 
Connaissant chacun des codes hexadécimaux envoyés par la télécommande, nous pouvons les traiter et les utiliser dans des conditions en fonction de leur valeur.
Si le bouton 1 est pressé, alors nous entrons dans le 1er mode d’affichage qui s’exécute à l’infini.
Pour pouvoir sortir de cette boucle infinie et changer de mode d’affichage, nous utilisons une fonction d’interruption sur Arduino : Lorsque l’Arduino « observe » un changement d’état au niveau du pin du capteur infrarouge, elle sort instantanément de la boucle et exécute une fonction dite d’interruption. 
Cette fonction va nous permettre de modifier les conditions d’accès à la boucle infini while pour en sortir et permettre de choisir un nouveau mode.


# III-	Installation murale et accessoire

Une fois la conception terminée, nous pouvons accrocher le cercle à un mur de la manière que l’on souhaite.
Pour relier les fils à l’Arduino sans rallonger leur longueur nous pouvons réaliser en 3D un petit rangement sobre ayant la place de stocker la carte et des fentes pour laisser passer les fils et le capteur infrarouge.

![Image1](https://user-images.githubusercontent.com/92324336/139710728-c0301627-bac6-414d-96aa-6ac87e7cdb43.png)

 
![20211030_112417_12090559320544](https://user-images.githubusercontent.com/92324336/139710515-c103ab78-5641-4859-9b75-07b7dc969638.gif)

