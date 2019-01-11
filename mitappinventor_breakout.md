# Versió del joc "Breakout" amb MIT App Inventor
En aquest tutorial es desenvoluparà una primera versió simple del mític joc "Breakout" amb 
l'eina [MIT App Inventor](http://appinventor.mit.edu).

![Breakout Atari](/assets/mit_breakout/breakout.png)

Aquesta primera versió estarà formada per només dues pantalles:
* **Screen1**. Pantalla d'inici amb un botó per començar a jugar i un per tancar l'aplicació.
* **scrNivell1**. El primer nivell del joc.

## Pantalla d'inici "Screen1"
### Disseny de la pantalla
Formada per un logo i dos botons.

![Pantalla inici - Disseny](/assets/mit_breakout/srcInici.png)

Col·loquem els tres objectes dins una dispossició vertical i, entre ells, posem dispossicions horitzontals amb una alçada fixa per tal de crear una petita separació.

![Separació entre elements](/assets/mit_breakout/srcIniciSeparacio.png)

### Programació
Molt simple, el botó de jugar canvia de pantalla i el de sortir tanca l'aplicació.

![Pantalla inici - Programació](/assets/mit_breakout/progInici.png)

## Pantalla de joc del primer nivell "scrNivell1"
### Disseny de la pantalla
Formada pels següents elements:
* etqNivell. Etiqueta estàtica que indica el nivell de joc actual.
* etqVides. Etiqueta que indica el nombre de vides.
* Lienzo1. Llenç principal del joc.
* sprBarra.

**Per moure la barra mitjançant moviment de mòbil utiltizar acelerometro**
![Programació acelerometro](/assets/mit_breakout/acelerometro.png)
