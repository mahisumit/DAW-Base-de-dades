![LogoMongoDB](https://github.com/mahisumit/DAW-BaseDeDades/blob/main/4.%20Base%20de%20dades%20objecte%20relacionals%20(UF4)/assests/MongoDB_Logo.png)
***

# Característiques clau de MongoDB:

<b>1. Model de dades orientat a documents:</b> MongoDB emmagatzema dades en documents BSON (una extensió binària de JSON). Cada document és una col·lecció de parelles clau-valor, la qual cosa permet una estructura de dades flexible.<br><br>
<b>2. Esquema flexible:</b> A diferència de les bases de dades relacionals, MongoDB no requereix definir un esquema fix per endavant. Això permet emmagatzemar documents amb estructures diferents en la mateixa col·lecció.<br><br>
<b>3. Escalabilitat horitzontal:</b> MongoDB està dissenyat per escalar horitzontalment utilitzant sharding, una tècnica de partició de dades que distribueix dades entre múltiples màquines.<br><br>
<b>4. Alta disponibilitat:</b> Utilitza rèpliques (replica sets) per assegurar la redundància i la recuperació automàtica de fallades.<br><br>
<b>5. Indexació:</b> Ofereix funcionalitats avançades d'indexació per millorar el rendiment de les consultes.<br><br>
<b>6. Agregació:</b> Proporciona un potent framework d'agregació per processar i analitzar dades.<br><br>

 ***
 
# Comandes bàsiques de MongoDB

## Avantatges de MongoDB:

* <b>Flexibilitat:</b> L'esquema dinàmic permet canvis ràpids en l'estructura de dades sense necessitat de migracions complexes.
* <b>Escalabilitat:</b> Dissenyat per escalar horitzontalment, ideal per a grans volums de dades i aplicacions de gran escala.
* <b>Facilitat d'ús:</b> La sintaxi JSON-like és intuïtiva i fàcil de treballar per a desenvolupadors.

## Desavantatges de MongoDB
* <b>Consistència:</b> Com moltes bases de dades NoSQL, MongoDB segueix el model de consistència eventual, que pot no ser adequat per a totes les aplicacions.
* <b>Transaccions limitades:</b> Les operacions de transaccions multi-document van ser introduïdes més recentment i no són tan robustes com en les bases de dades SQL tradicionals.
