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
* **sprLevelUp**. Imatge que sortirà al finalitzar el nivell (trencar tots els blocs).
* **sprGameOver**. Imatge que sortirà al finalitzar el joc.
* **sprBlocG1, sprBlocG2, sprBlocV1, sprBlocV2**. Els blocs de colors (G=Groc i V=Vermell) que cal trencar amb la pilota. En aquesta primera versió del joc només col·locarem quatre blocs.
* **rljInici**. Rellotge per provocar un retard d'uns segons al carregar la pàgina i col·locar els objectes. A l'adaptar la posició dels objectes de manera dinàmica a les dimensions de la pantalla podem tindre problemes si no esperem uns segons a que l'aplicació calculi l'alçada i amplada de la pantalla.
* **rljGameOver**. Amb aquest rellotge mostrarem la imatge *sprGameOver* durants uns segons i després obrirem la finestra inicial.

A la següent imatge es poden apreciar les disposicions utilitzades per col·locar tots els elements.

![Pantalla 1r nivell - Disseny](/assets/mit_breakout/scrNivell1.png)

### Programació
Comencem la programació creant tres variables necessàries pel control del joc:
* **vides**. Les vides que tindrà el jugador.
* **num_blocs**. Li restarem un cada cop que es trenqui un bloc. D'aquesta manera podem controlar el final del nivell.
* **vel_pilotes**. Velocitat inicial de la pilota. En properes versions podem millorar el joc fent que cada cert temps s'incrementi el valor d'aquesta variable.

![Variables inicials](/assets/mit_breakout/variables_scrNivell1.png)

Crearem tres procediments per inicialitzar la posició dels blocs, la barra i la pilota. Els [procediments](http://appinventor.mit.edu) són agrupacions de codi que poden ser executades des de qualsevol altre lloc. Ens serveixen per organitzar i reaprofitar el codi.
* **iniBarra**. Posiciona la barra a baixa de la pantalla i al centre.
![Procediment inicialitza barra](/assets/mit_breakout/iniBarra.png)
* **iniPilota**. Posiciona la pilota al centre de la pantalla, estableix la velocitat i comença a moure-la.
![Procediment inicialitza pilota](/assets/mit_breakout/iniPilota.png)
* **iniBlocs**. Posiciona els quatre blocs.
![Procediment inicialitza blocs](/assets/mit_breakout/iniBlocs.png)

Anem a programar l'inici del joc en carregar la pantalla. Aquí utilitzarem l'element **rljInici** per provocar un petit retard de 2 segons. El temps de retard l'hem assignat a la pantalla de disseny (*IntervaloDelTemporizador = 2000*). Un cop es dispara el rellotge (han passat els 2 segons) és molt important desactivar-lo per evitar que s'executi contínuament.

![Inici srcNivell1](/assets/mit_breakout/inici-scrNivell1.png)

Programem el moviment de la barra.

![Moviment barra](/assets/mit_breakout/moviment-barra.png)

Amb el moviment de la pilota tenim més opcions a programar: quan toca una vora qualsevol, quan toca la vora inferior, al tocar la barra i al tocar un bloc. El cas de tocar un bloc el programarem més endavant dins el codi del bloc, anem ara a programar la resta d'opcions. Pel moviment de la pilota cal tindre en compte els valors de les vores i direccions en MIT App Inventor, en la següent imatge es mostren aquests valors.

![Vores i direccions](/assets/mit_breakout/vores_direccions.jpg)

Quan la pilota toca la barra.

![Pilota toca la barra](/assets/mit_breakout/tocaBarra.png)

Quan toca una vora hem de tindre en compte de si es tracta de la vora inferior, en aquest cas hem de treure una vida i inicialitzar la posició de la pilota. En treure una vida hauriem de comprovar el moment en que es produeix el final de joc. Crearem un procediment per treure vides.

![Procediment treu vida](/assets/mit_breakout/treuVida.png)

Ja podem programar quan la pilota toca una vora.

![Pilota toca vora](/assets/mit_breakout/tocaVora.png)

L'última part que ens falta és quan la pilota col·lisiona un bloc. En aquest haurem de programar bloc a bloc (en aquesta primera versió en tenim 4) que desapareixi i faixi rebotar la pilota. A part, sempre que es trenqui un bloc haurem de disminuir la variable amb el nombre de blocs disponibles (*num_blocs*) i controlar el final del nivell. Per aquestes dues darreres accions crearem un procediment.

![Procediment trenca bloc](/assets/mit_breakout/trencaBloc.png)

Ara ja podem programar el trencament del bloc en concret. El següent codi s'ha de fer per tots els blocs disponibles en el nivell (només es mostra el trencament del bloc *sprBlocG1*).

![Trenca Bloc G1](/assets/mit_breakout/trencaBlocG1.png)

## Properes versions del joc
Hem desenvolupat una versió molt bàsica del joc. En properes versions podríem aplicar varies millores:
* Afegir més blocs al primer nivell.
* Augmentar la velocitat de la pilota cada cert temps.
* Crear més nivells.
* Crear blocs especials amb premis. Al trencar aquests blocs cauen premis que es poden agafar amb la barra. Alguns exemples de premis podrien ser vides, opció de disparar, dues pilotes, barra més gran, ...
* Fer moure la barra mitjançant el moviment del mòbil. Per fer-ho cal afegir un objecte del tipus *Sensores > Acelerómetro* a la pantalla i programar el moviment en horitzontal per la pantalla:
![Programació acelerometro](/assets/mit_breakout/acelerometro.png)


