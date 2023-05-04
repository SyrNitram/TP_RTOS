# TP_RTOS



Q13 : PB9 est tirée à la masse par la resistance de 100k car ce pin coeespond à BOOT0.
Lorsque ce pin est à 0 le boot s'effectue depuis la memoire flash si le bit de config nBOOT_SEL est à 0.


Q14 : L1, C5, C7 forment un filtre passe-bas. ce filtre permet d'éliminer les parasite eventuels sur l'alimenttion avant que la tension de sortie serve de reference à l'ADC du microcontrôleur (VDDA).

# Le reste
Q3 : La première page indique que Cin et Cout doivent être superieurs à 0.47uF. La page 3 donne une valeur typique de 1uF.

Q5 : Page 25.

Q6 : CS est l'entrée chip select active à l'état bas. elle permet d'activer la communication spi avec ce composant.

Q7 : La broche LDAC permet de déclencher le changement de la tension de sortie quand l'entrée est à 0.

Q8 : Le signal MISO n'est pas utilisé car le MCP ne revoit pas d'information au microcontrôleur.

Q10 : Le pinout du connecteur SWD se trouve dans la documentation du STlink page 26.

# Affectation des empreintes

Q3 : Il s'agit de la taille du composant en dixième de pouce (ex : 0805 = 0.08 x 0.05 in).

Q4 : 	LQFP : Low Profile Quad Flat Package, est un type de boîtier de circuit intégré destiné à être directement soudé sur circuit imprimé.
	SOT : Small Outline Transistor, c'est un package fréquement utilisé pour les régulateurs de tension.
	SOIC : Small Outline Integrated Circuit, ce package est equivalent au boitier DIP mais est quasiment deux fois plus petit.
	
# LED simple

2. On souhaite une frequence de PWM de 1kHz avec une résolution de 8bits soit 256 valeurs. L'horloge choisie est à 16MHz, on sait que l'on veut un ARR de 255, on en deduit la valeur du prescaler PSC = 16000/256 = 62,5 . On choisis PSC = 63. 

#LED avec timer

3. PSC vaut 16 pour obtenir un compteur à 1MHz, on choisis ensuite un ARR de 1000 pour que le compteur se reset toutes les ms. on ective ensuite l'interruption sur reset.

6. La routine se trouve dans la fonction void TIM21_IRQHandler(void) dans stm32l0xx_it.c,elle est vide.

7. Il manque la remise à zero du flag d'interruption

8. l'interruption va se declencher en boucle si le flag n'est pas remis à 0.

9. Il faut remettre à 0 le flag.

#UART

5. La variable envoyer n'est pas le pointeur vers la variable mais la variable elle-même.
