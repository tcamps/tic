# Introducció al Framework Foundation
*Foundation* és un Framework HTML i CSS. Un Framework és un entorn de treball que ens facilita l'utilització d'una metodologia de desenvolupament i ens subministra uns elements ja creats com, en aquest cas, formularis, pàgines d'inici de sessió, menús de navegació, ...

## Instal·lació de Foundation
Baixem la versió completa de la següent pàgina i descomprimim l'arxiu:
[Download Foundation](https://download.get.foundation/sites/download/)

Tindrem una carpeta *css* i *js* amb els arxius d'estil (CSS) i Javascript respectivament, així com un arxiu *index.html* amb una primera pàgina de mostra.

## Creacio d'una primera pàgina
Dins la carpeta arrel creem un arxiu *exemple.html* amb el següent contingut bàsic:

~~~
<!doctype html>
<html class="no-js" lang="ca" dir="ltr">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="x-ua-compatible" content="ie=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Foundation for Sites</title>
    <link rel="stylesheet" href="css/foundation.css">
    <link rel="stylesheet" href="css/app.css">
  </head>
  <body>
  </body>
</html>
~~~

A la pàgina de [documentació de *Foundation*](https://get.foundation/sites/docs/) hi ha explicats tots els elements que podem utilitzar. Anem a fer un petit exemple afegit un barra de navegació, un contingut separat amb dos columnes i un botó.

### Barra de navegació
A la pàgina de documentació anem a *[Navigation --> Top Bar](https://get.foundation/sites/docs/top-bar.html)* i agafem el primer exemple. Copiem el codi l'afegim a la nostra pàgina. Treurem el menú desplegable sota la primera opció, la caixa de cerca de la dreta i personalitzem el títol i els enllaços. Com a exemple, ens quedaria el següent codi:
~~~
<div class="top-bar">
  <div class="top-bar-left">
    <ul class="dropdown menu" data-dropdown-menu>
      <li class="menu-text">Títol lloc</li>
      <li><a href="#">Inici</a></li>
      <li><a href="#">Els meus projectes</a></li>
      <li><a href="#">Contacte</a></li>
    </ul>
  </div>
</div>
~~~

### Sistema de quadrícula
El sistema de quadrícula ens ajuda a repartir el contingut del nostre lloc web en cel·les que poden ser col·locades horitzontalment (files) i/o verticalment (columnes) i que es redimensiones i recol·loquen tenint en compte la mida de la pantalla. El sistema de quadrícula CSS més actual és el *Flexbox Grid*.

En el nostre exemple volem una columna principal amb el contingut i una columna més petita a la dreta amb, per exemple, les darreres notícies publicades al nostre lloc. Per dissenyar el contingut utilitzarem el sistema de quadrícula *XY Grid* de *Foundation*: [*General --> XY Grid*](https://get.foundation/sites/docs/xy-grid.html). Anem al primer exemple (*Basics*) i agafem el tercer exemple, però en el nostre cas invertim les columnes de manera que ens quedi la primera més gran que la segona i hi afegim una mica de contingut.
~~~
<div class="grid-x">
  <div class="cell medium-6 large-8">
    <h1>Contingut principal</h1>
  </div>
  <div class="cell medium-6 large-4">
    Darreres notícies publicades
    <ul>
      <li>Webs desenvolupades</li>
      <li>Introducció a Python</li>
      <li>HTML5 i CSS3</li>
    </ul>
  </div>
</div>
~~~

Tot el codi anterior el posarem dins un [*Grid Container*](https://get.foundation/sites/docs/xy-grid.html#grid-container) a fi de poder modificar l'amplada total del contingut.
~~~
<div class="grid-container">
  <div class="grid-x">
    ...
  </div>
</div>
~~~

### Personalització dels estils
Podem personalitzar els estils dels diferents elements HTML afegint les nostres pròpies classes CSS. Creem un nou full d'estills *personal.css* dins la carpeta *css* i creem les següents classes:
~~~
.contingut-principal {
  background-color: #ffffff;
}

.columne-dreta {
  background-color: #fff2f2;
  padding: 10px;
}

.cos {
  max-width: 1500px;
  margin-top: 20px;
}
~~~

I afegim la referència al nou full i a les classes en l'arxiu *exemple.html*. Finalment, el codi HTML ha de quedar així:
~~~
<!doctype html>
<html class="no-js" lang="ca" dir="ltr">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="x-ua-compatible" content="ie=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Foundation for Sites</title>
    <link rel="stylesheet" href="css/foundation.css">
    <link rel="stylesheet" href="css/app.css">
    **<link rel="stylesheet" href="css/personal.css">**
  </head>
  <body>
    <div class="top-bar">
      <div class="top-bar-left">
        <ul class="dropdown menu" data-dropdown-menu>
          <li class="menu-text">Títol lloc</li>
          <li><a href="#">Inici</a></li>
          <li><a href="#">Els meus treballs</a></li>
          <li><a href="#">Contacta</a></li>
        </ul>
      </div>
    </div>
    <div class="grid-container cos">
      <div class="grid-x">
        <div class="cell medium-6 large-8 contingut-principal">
          <h1>Contingut principal</h1>
        </div>
        <div class="cell medium-6 large-4 columne-dreta">
          Darreres notícies publicades
          <ul>
            <li>Webs desenvolupades</li>
            <li>Introducció a Python</li>
            <li>HTML5 i CSS3</li>
          </ul>
        </div>
      </div>
    </div>
  </body>
</html>
~~~
