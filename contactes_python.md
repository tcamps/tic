# Gestió de 'Contactes' amb Pyhton i MySQL
En el següent exemple veurem un cas senzill de gestió d'una base de dades amb una sola taula de contactes mitjançant Python des de la consola.

Partim amb una base de dades MySQL 'contactes' amb una sola taula 'contactes' amb la següent aparença:

`SELECT * FROM contactes;`

|id|nom|cognoms|telf|email|
|--|---|-------|----|-----|
|1|Goku|Son|666666666|goku@email.com|
|2|Satanas|Cor Petit|669669669|satanas@email.com|
|3|Arale|Norimaki|678987654|arale@email.com|

## Programació per capes
A fi de millorar el disseny de la nostra aplicació la desenvoluparem utilitzant tres capes:
1. Capa de presentació. En aquest cas serà una interfície per consola i estarà formada per un sol arxiu: **icontactes.py**
2. Capa de lògica de negoci. Una petita llibreria amb les consultes SQL i retornant les dades necessàries. Formada per l'arxiu **contactes.py**
3. Capa de dades. La base de dades i l'accés a ella. Estarà formada per una petita llibreria que connectarà a la base de dades i rebrà consultes SQL que seran executades. Formada per l'arxiu **bd.py**

## Llibreria d'accés a la base de dades - bd.py
Primer de tot crearem un arxiu anomenat **bd.py** el qual s'encarregarà de connectar amb la base de dades del projecte i executar una consulta SQL. Si la consulta és un *SELECT* retornarà una col·lecció de dades amb totes les files del resultat. En cas de tractar-se d'una consulta de modificació *INSERT*, *UPDATE* o *DELETE* no retornarà res. 
```
import MySQLdb

# Variables amb les dades d'accés
BD_SERVIDOR = ''
BD_USUARI = ''
BD_CONTRASENYA = ''
BD_NOMBD = ''

#Funció simple que connecta amb la base de dades i executa una consulta
#En cas de 'SELECT' retorna una col·leció de dades, en la resta de casos no retorna res
def executa_consulta(consulta=''):
    # Conectar a la base de dades i crear un cursor
    dades = [BD_SERVIDOR, BD_USUARI, BD_CONTRASENYA, BD_NOMBD]
    conn = MySQLdb.connect(*dades)
    cursor = conn.cursor()

    # Executa la consulta rebuda
    cursor.execute(consulta)

    # Comprova si és consulta de dades o modificació
    if consulta.upper().startswith('SELECT'):
        # Crea la col·leció de dades amb el resultat
        resultat = cursor.fetchall()
    else:
        # Fa efectiva l'escriptura de dades i no retorna res
        conn.commit()
        resultat = None

    # Tancar el cursor i la connexió
    cursor.close()
    conn.close()

    # Retorna les dades (o res en cas d'escriptures)
    return resultat
```
El codi és molt simple, però per el cas que tractem és suficient. Es pot reaprofitar l'arxiu simplement adaptant les quatre variables d'accés a cada projecte.

## Interacció interfície i base de dades - contactes.py
En l'arxiu **contactes.py** hi haurà les funcions que seran cridades des de la interfície per fer la gestió de contactes: *llistar contactes*, *afegir contacte*, *retornar contacte*, *modificar contacte* i *eliminar contacte*. Aquest arxiu farà ús de la llibreria **bd.py** per executar consultes SQL a la base de dades.

Primer de tot, importem la llibreria **bd.py**:
`import bd.py`

Anem a crear una funció que retorni un llistat de tots els contactes disponibles a la base de dades:
```
def llistar_contactes():
    contactes = bd.executa_consulta('SELECT * FROM contactes')
    return contactes
```
També hem d'afegir una segona funció que rep com a paràmetres un nou contacte i l'afegeix a la base de dades:
```
def nou_contacte(nom, cognoms, telf, email):
    bd.executa_consulta("INSERT INTO contactes(nom, cognoms, telf, email) 
    VALUES('"+ nom +"', '"+ cognoms +"', '" + telf + "', '" + email + "')")
```
Per completar la gestió ens faltarien, com a mínim, dos funcions més:
* Editar un contacte. Funció que rep com a paràmetres les dades d'un contacte existent (és molt important l'identificador) i realitza una modificació.
* Eliminar un contacte. Funció que rep com a paràmetre l'identificar d'un contacte existent i l'elimina.
## Interfície de l'aplicació - icontactes.py
