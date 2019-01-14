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
* **etqNivell**. Etiqueta estàtica que indica el nivell de joc actual.
* **etqVides**. Etiqueta que indica el nombre de vides.
* **Lienzo1**. Llenç principal del joc.
* **sprBarra**. La barra inferior del joc que mourà el jugador.
* **sprPilota**. La pilota del joc.
* **sprGameOver**. Imatge que sortirà al finalitzar el joc.
* **sprBlocG1, sprBlocG2, sprBlocV1, sprBlocV2**. Les barres de colors (G=Groc i V=Vermell) que cal trencar amb la pilota. En aquesta primera versió del joc només col·locarem quatre barres.
* **rljInici**. Rellotge per provocar un retard d'uns segons al carregar la pàgina i col·locar els objectes. A l'adaptar la posició dels objectes de manera dinàmica a les dimensions de la pantalla podem tindre problemes si no esperem uns segons a que l'aplicació calculi l'alçada i amplada de la pantalla.
* **rljGameOver**. Amb aquest rellotge mostrarem la imatge *sprGameOver* durants uns segons i després obrirem la finestra inicial.

A la següent imatge es poden apreciar les disposicions utilitzades per col·locar tots els elements.

![Pantalla 1r nivell - Disseny](/assets/mit_breakout/scrNivell1.png)

**Per moure la barra mitjançant moviment de mòbil utiltizar acelerometro**
![Programació acelerometro](/assets/mit_breakout/acelerometro.png)
