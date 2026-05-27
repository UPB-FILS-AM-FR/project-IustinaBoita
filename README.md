# Jeu 2048

| | |
|-|-|
|`Author` | Iustina Boiță

## Description

Mon projet est une recréation du jeu 2048, un jeu où, grâce à certaines commandes, les multiples de 2 s'additionnent pour former des nombres plus grands. Le but du jeu est de faire un maximum de paires de nombres qui fusionnent pour atteindre le score le plus élevé possible. Je l'ai adapté de manière à ce que le joueur puisse contrôler le jeu par les mouvements de la main (sur les axes haut-bas et droite-gauche), sans avoir à appuyer sur un bouton pour déplacer les nombres. Chaque mouvement déclenchera un signal sonore (un bip) provenant d'un buzzer connecté. 
Chaque niveau a un objectif à atteindre : 
si le joueur passe au niveau suivant, le buzzer émet deux bips courts, 
si le joueur atteint le dernier niveau, le buzzer émettra trois bips pour annoncer la fin du jeu,
si le joueur remplit la grille et qu'aucune autre action n'est possible, la partie se termine et le jeu émet un bip long d'une seconde et demie.
Le joueur peut réinitialiser la partie en appuyant sur la touche « R » s'il souhaite recommencer le niveau depuis le début. Chaque score est sauvegardé. 
De plus, chaque mouvement, niveau, score ou information est affiché en temps réel sur l'écran pendant le jeu.

## Motivation

Depuis toute petite, je jouais à ce jeu et j'aimais faire des calculs. Je faisais des compétitions avec mes camarades de classe pour obtenir le score le plus élevé à chaque fois qu'un nouveau nombre apparaissait sur l'écran. 
Je l'ai réalisé parce que c'est un jeu de logique qui fait travailler l'esprit et qui entraîne la réflexion en termes d'attention, de calculs et de stratégie. 
Grâce à ce jeu, les joueurs peuvent s'amuser tout en se défiant, mais ils améliorent aussi leur sens de la stratégie, renforcent leur attention, apprennent à prendre des décisions rapides et perfectionnent leurs compétences en calcul mental rapide pour les multiples de 2.

## Architecture

Le projet consiste en une implémentation du jeu 2048, où l'interaction de l'utilisateur est entièrement basée sur le mouvement gestuel par l'inclinaison de la carte. Le système est structuré ainsi:
Le contrôle: La carte Arduino Nano constitue l'unité centrale de traitement qui exécute la logique du jeu 2048, interprète les données du capteur, met à jour le score, et gère et fournit les informations sur le jeu.
La détection du mouvement: L'accéléromètre MMA8451 dispose de 3 axes: X, Y et Z. Il mesure l'accélération gravitationnelle sur ces axes pour détecter l'angle ou la direction d'inclinaison de la main et transmet ces informations via la communication filaire avec la carte Arduino, à travers les broches dédiées SDA - A4 et SCL - A5.
Le son: Le buzzer utilisé est un modèle actif et est connecté à la broche numérique D8. Son rôle est d'émettre différents signaux sonores par des impulsions en temps réel pour accompagner les actions de l'utilisateur.
Le module d'affichage: J'ai utilisé l'application Arduino IDE. La carte est connectée par un câble USB à l'ordinateur portable. La fonction Serial Monitor sert d'écran principal où la matrice de jeu 4x4 est dessinée de manière dynamique et permet la réception des commandes du clavier, c'est-à-dire la fonction de réinitialisation (Reset) via la touche „R”  et ENTER.

Initialisation: Je connecte le câble USB de l'Arduino à mon laptop. L'Arduino démarre le capteur de mouvement. Pendant les 2 premières secondes, lorsque la carte est immobile, l'Arduino lit très rapidement la position de ma main à 20 reprises. Il calcule une moyenne, puis établit la position de référence de la main et de la carte. Il s'agit de la position initiale. Tout mouvement futur par rapport à cette position sera considéré comme une commande de jeu.

Traitement des données: Dans la boucle principale (loop), le système lit constamment les angles d'inclinaison. Pour éviter les mouvements chaotiques causés par le tremblement de la main, le code implémente un mécanisme de filtrage logiciel par seuils différenciés (Hystérésis).
Le seuil d'activation (30): Un déplacement n'est déclenché que si l'inclinaison sur un axe dépasse la valeur de 30. À ce moment-là, le système du jeu bloque les nouvelles commandes pour éviter que plusieurs mouvements ne se produisent en même temps (blocatMiscare = true).
Le seuil de retour (18): Le système reste bloqué et refuse d'autres mouvements tant que le joueur ne ramène pas la carte vers la position horizontale (en dessous de la valeur de 18). Cela garantit l'exécution d'un seul mouvement par inclinaison et offre un contrôle parfait de la carte.

La logique du jeu et les sons: Si le mouvement est validé, l’Arduino déplace les nombres sur l’écran dans la direction choisie (Haut, Bas, Gauche ou Droite) via la fonction muta(dirX, dirY). Les éléments de la matrice sont translatés et fusionnés dans la mémoire RAM, puis une nouvelle pièce est générée aléatoirement dans les espaces restés libres et/ou les nombres égaux sont combinés (par exemple, deux 2 deviennent un 4).
Immédiatement après la mise à jour, le système génère les réponses de sortie visuelles et sonores.
Visuel : Il envoie via le port Série l’état mis à jour de la matrice, le score actuel et le score le plus élevé enregistré (Record), en dessinant un tableau dans le Moniteur Série.
Sonore : Il active le buzzer via la broche D8 avec des signaux sonores clairement différenciés : 1 bip court (60ms) pour un mouvement normal réussi, 2 bips successifs lorsque le seuil d’un nouveau niveau est atteint (Level Up : 16, 64, 128, 512), 3 bips longs au moment où le jeu est entièrement gagné.
Le système du jeu reste dans cet état de surveillance continue, tout en étant capable d’interrompre instantanément la partie et de la réinitialiser à l’état initial s'il reçoit le caractère « r » ou « R » depuis l’ordinateur, la touche attribuée à la commande de Reset.

### Block diagram

<img width="2800" height="2126" alt="Block Diagram - joc" src="https://github.com/user-attachments/assets/0269576a-a1c3-47c2-b73c-82a179396e63" />


### Schematic

<img width="2940" height="1912" alt="image" src="https://github.com/user-attachments/assets/53d206f6-0ff0-4a28-9b3e-615e2098d1f2" />


### Components


<!-- This is just an example, fill in with your actual components -->

| Device | Usage | Price |
|--------|--------|-------|
| Activ Buzzer | Buzzer | [1.5 RON](https://www.optimusdigital.ro/ro/audio-buzzere/635-buzzer-activ-de-3-v.html?search_query=buzzer&results=61) |
| Push Button | Button | [1 RON](https://www.optimusdigital.ro/ro/butoane-i-comutatoare/1119-buton-6x6x6.html?search_query=buton&results=222) |
| Jumper Wires | Connecting components | [7 RON](https://www.optimusdigital.ro/ro/fire-fire-mufate/884-set-fire-tata-tata-40p-10-cm.html?search_query=set+fire&results=110) |
| Breadboard | Project board | [10 RON](https://www.optimusdigital.ro/ro/prototipare-breadboard-uri/8-breadboard-830-points.html?search_query=breadboard&results=145) |

### Libraries

<!-- This is just an example, fill in the table with your actual components -->

| Library | Description | Usage |
|---------|-------------|-------|
| [lib-name1](link-to-lib) | official description of the lib | Used for accesing the peripherals of the microcontroller  |
| [lib-name2](link-to-lib) | official description of the lib | Used for accesing the peripherals of the microcontroller  |

## Log

<!-- write every week your progress here -->

### Week 6 - 12 May

### Week 7 - 19 May

### Week 20 - 26 May


## Reference links

<!-- Fill in with appropriate links and link titles -->

[Tutorial 1](https://www.youtube.com/watch?v=wdgULBpRoXk&t=1s&ab_channel=BenEater)

[Article 1](https://www.explainthatstuff.com/induction-motors.html)

[Link title](https://projecthub.arduino.cc/)
