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
Un sol arxiu bd.py format pel següent codi:
```
import MySQLdb

DB_HOST = 'tcamps.mysql.pythonanywhere-services.com'
DB_USER = 'tcamps'
DB_PASS = 'tcampstcamps'
DB_NAME = 'tcamps$contactes'

#Funció simple que connecta amb la base de dades i executa una consulta
#En cas de 'SELECT' retorna una col·leció de dades, en la resta de casos no retorna res
def run_query(query=''):
    datos = [DB_HOST, DB_USER, DB_PASS, DB_NAME]

    conn = MySQLdb.connect(*datos) # Conectar a la base de dades

    cursor = conn.cursor()         # Crear un cursor

    cursor.execute(query)          # Executar una consulta

    if query.upper().startswith('SELECT'):
        data = cursor.fetchall()   # Crea la col·leció de dades data amb totes les dades
    else:
        conn.commit()              # Fa efectiva l'escriptura de dades
        data = None

    cursor.close()                 # Tanca el cursor
    conn.close()                   # Tanca la connexió

    return data                    # Retorna les dades (o res en cas d'escriptures)
```
