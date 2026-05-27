# Jeu 2048

| | |
|-|-|
|`Author` | Iustina Boiță

## Description
Mon projet est une recréation du jeu 2048, un jeu où, grâce à certaines commandes, les multiples de 2 s'additionnent pour former des nombres plus grands. Le but du jeu est de faire un maximum de paires de nombres qui fusionnent pour atteindre le score le plus élevé possible. Je l'ai adapté de manière à ce que le joueur puisse contrôler le jeu par les mouvements de la main (sur les axes haut-bas et droite-gauche), sans avoir à appuyer sur un bouton pour déplacer les nombres. Chaque mouvement déclenchera un signal sonore (un bip) provenant d'un buzzer connecté. Chaque niveau a un objectif à atteindre : si le joueur passe au niveau suivant, le buzzer émet deux bips courts, et si le joueur remplit la grille et qu'aucune autre action n'est possible, la partie se termine et le jeu émet trois bips. 
Le joueur peut réinitialiser la partie en appuyant sur la touche « R » s'il souhaite recommencer le niveau depuis le début. Chaque score est sauvegardé. 
De plus, chaque mouvement, niveau, score ou information est affiché en temps réel sur l'écran pendant le jeu.

## Motivation




## Architecture




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
