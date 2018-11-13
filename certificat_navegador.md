# Certificats digitals i HTTPS
Quan obrim una pàgina web utilitzant el protocol HTTPS vol dir que el servidor web al qual ens connectem té un certificat digital. 
Aquest certificat digital té dues funcions:
1. **Confirmar la identitat del servidor web**. Una tercera empresa de confiança, l'entitat certificadora, ha emès aquest certificat 
i això ens permet estar segurs que la pàgina web és autèntica.
2. **Xifrar la comunicació**. El servidor web propietari del certificat digital tindrà una parella de claus (pública i privada) 
amb les quals es podrà xifrar de manera asimètrica.

Amb qualsevol navegador web modern podem veure els detalls d'aquest certificat digital. Per exemple, anem a la pàgina d'inici del 
**GestIB** (Aplicació per la Gestió Educativa de les Illes Balears) i el cadenat verd del costat de la URL ens indicarà que el servidor té un certificat digital.

![Cadenat verd](/assets/certificat_digital/certificat1.jpg)

Cliquem damunt el cadenat i al costat de l'adreça hi haurà una fletxa per veure els detalls del certificat (*Mostra el detall de la connexió*)

![Detalls certificat](/assets/certificat_digital/certificat2.jpg)

En un primer moment ens indicarà que el certificat és emés per FNMT-RCM i devall tindrem l'opció de veure'l amb detall (*Més informació*)

![Més informació](/assets/certificat_digital/certificat3.jpg)

En la següent pantalla ja podem veure el certificat sencer (*Mostra el certificat*)

![Mostra el certificat](/assets/certificat_digital/certificat4.jpg)

Per exemple, podem veure les dades completes de l'empresa certificadora (*Emès per*)

![Emès per](/assets/certificat_digital/certificat5.jpg)

I la clau pública de la pàgina web (*Clau pública personal*)

![Clau pública personal](/assets/certificat_digital/certificat6.jpg)
