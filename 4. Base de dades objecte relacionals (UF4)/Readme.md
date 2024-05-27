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
 
# Avantatges de MongoDB:

* <b>Flexibilitat:</b> L'esquema dinàmic permet canvis ràpids en l'estructura de dades sense necessitat de migracions complexes.
* <b>Escalabilitat:</b> Dissenyat per escalar horitzontalment, ideal per a grans volums de dades i aplicacions de gran escala.
* <b>Facilitat d'ús:</b> La sintaxi JSON-like és intuïtiva i fàcil de treballar per a desenvolupadors.

# Desavantatges de MongoDB
* <b>Consistència:</b> Com moltes bases de dades NoSQL, MongoDB segueix el model de consistència eventual, que pot no ser adequat per a totes les aplicacions.
* <b>Transaccions limitades:</b> Les operacions de transaccions multi-document van ser introduïdes més recentment i no són tan robustes com en les bases de dades SQL tradicionals.

*** 

# Comandes bàsiques de MongoDB: 

## 1. Inserció de documents: 

 ```js
db.collection.insertOne(
    {
        "name": "Alice",
        "age": 28,
        "address": {
            "street": "123 Main St",
            "city": "Anytown",
            "zipcode": "12345"
        },
        "hobbies": ["reading", "hiking", "coding"]
    }
);

db.collection.insertMany([
    {
        "name": "Bob",
        "age": 32,
        "address": {
            "street": "456 Elm St",
            "city": "Othertown",
            "zipcode": "67890"
        },
        "hobbies": ["gaming", "cooking"]
    },
    {
        "name": "Charlie",
        "age": 25,
        "address": {
            "street": "789 Oak St",
            "city": "Elsewhere",
            "zipcode": "11223"
        },
        "hobbies": ["swimming", "traveling"]
    }
]);
 ```

## 2. Consulta de documents:
 ```js
 // Consulta simple
 db.collection.find({"name": "Alice"});
 
 // Consulta amb condicions
 db.collection.find({"age": { $gt: 30 }});
 
 // Consulta amb projecció
 db.collection.find({"age": { $gt: 30 }}, { "name": 1, "address.city": 1, "_id": 0 });
 ```

## 3. Actualització de documents:
 ```js
 // Actualització d'un sol document
 db.collection.updateOne(
     { "name": "Alice" },
     { $set: { "age": 29 } }
 );
 
 // Actualització de múltiples documents
 db.collection.updateMany(
     { "age": { $lt: 30 } },
     { $set: { "status": "young adult" } }
 );
 ```

## 4. Eliminació de documents:
 ```js
  // Eliminació d'un sol document
  db.collection.deleteOne({ "name": "Charlie" });
  
  // Eliminació de múltiples documents
  db.collection.deleteMany({ "age": { $gte: 30 } });
 ```

## 5. Agregació:
L'agregació en MongoDB es fa mitjançant el aggregate pipeline, que permet processar dades en diverses etapes.
 ```js
  db.collection.aggregate([
     { $match: { "age": { $gte: 25 } } },
     { $group: { _id: "$status", total: { $sum: 1 } } },
     { $sort: { total: -1 } }
 ]);
 ```

***

# Exemples d'ús:
Creació d'una col·lecció i inserció de documents.
 ```js
  use mydatabase;
  db.users.insertMany([
     { "name": "John Doe", "email": "john@example.com", "age": 25, "registered": true },
     { "name": "Jane Smith", "email": "jane@example.com", "age": 30, "registered": false },
     { "name": "Jim Brown", "email": "jim@example.com", "age": 35, "registered": true }
  ]);
 ```

Consulta avançada amb agregació.
 ```js
 db.users.aggregate([
     { $match: { "registered": true } },
     { $group: { _id: "$age", count: { $sum: 1 } } },
     { $sort: { count: -1 } }
 ]);
 ```

Índexs per millorar el rendiment.
 ```js
 // Crear un índex
 db.users.createIndex({ "email": 1 });
 
 // Llistar índexs
 db.users.getIndexes();
 ```
