# Versió del joc "T-Rex Game" amb Scratch

En aquest tutorial es desenvoluparà una primera versió simple del joc T-Rex que apareix al navegador Chrome quan falla la connexió a Internet.

![T-Rex Game](/assets/scratch_trex/t-rex-game.png)

## Moviment del terra

Per donar sensació de moviment hem de fer moure el terra. Hi ha varies tècniques per fer moure un fons / imatge de manera continua, en aquest cas utilitzarem la següent:
* Crear un personatge amb una imatge del terra que ocupi tota la pantalla, és a dir, amb una amplada de 480 píxels.
* Al començar el joc, es crearà una còpia d'aquest personatge.
* La primera copia es col·locarà a la posició 0, ocupant tota la pantalla, i la segona a la posició 480, just després de la primera.
* Cada personatge es mourà fins a completar -480 pases, just després les dues tornaran a la posició inicial.
* El nombre de pases a moure cada cop es calcularà amb una variable, d'aquesta manera en qualsevol moment es pot augmentar la velocitat del joc.

A continuació hi ha el codi necessari per desenvolupar aquest moviment:

![Moviment terra](/assets/scratch_trex/mov_terra.png)

## Moviment del personatge

Creem un nou personatge "dino" amb quatre vestits diferents, posant com a primer i per defecte el d'inici.

![Vestits dinosaure](/assets/scratch_trex/dino-vestits.png)

Per simular el moviment del dinosaure anem intercal·lant entre els dos vestits de caminar. Per definir el temps d'espera entre cada canvi de vestit utilitzem la variable de velocitat creada al principi. A més velocitat menys temps d'espera entre el canvi.

![Moviment dinosaure](/assets/scratch_trex/dino-moviment.png)
