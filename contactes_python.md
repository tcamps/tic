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
