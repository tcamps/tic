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

A la pàgina de documentació de *Foundation* hi ha explicats tots els elements que podem utilitzar: [Documentació de Foundation](https://get.foundation/sites/docs/) Anem a fer un petit exemple afegit un barra de navegació, un contingut separat amb dos columnes i un botó.

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
