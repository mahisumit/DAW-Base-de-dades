# Exercici 0 – Importació de la BD #

Importa els fitxers .json per la BD de [rrhh:](https://github.com/mahisumit/DAW-BaseDeDades/blob/main/4.%20Base%20de%20dades%20objecte%20relacionals%20(UF4)/DataBase/rrhh.zip). <br>
Passos: <br>
• Crea la BD [rrhh](https://github.com/mahisumit/DAW-BaseDeDades/blob/main/4.%20Base%20de%20dades%20objecte%20relacionals%20(UF4)/DataBase/bbdd_rrhh.sql) <br>
• Importa el fitxer departaments.json → col·lecció departaments <br>
• Importa el fitxer empleats.json → col·lecció empleats

## Exercicis $group: ##

1. Mostra la quantitat d’empleats per cada departament. Mostra id de departament i la quantitat.
   ```js

   ```

3. Si no ho has tingut en compte en l’exercici anterior. Només tingues en compte aquells empleats que estiguin en un departament.
   ```js

   ```

3. Ordena el resultat anterior per els departament de més a menys nombre d’empleats.
   ```js

   ```

4. De cada departament mostra el salari més alt. Mostra id de departament i el salari més alt.
   ```js

   ```

5. Quina és la massa salarial de cada departament? Mostra id de departament i la massa salarial.
   ```js

   ```

6. Només mostra aquells departaments que tinguin una massa salarial igual o superior a 19000.
   ```js

   ```

***

## Exercicis: ##

7. Redefineix el camp “historial_feines” perquè tingui el número de feines i no el detall de les feines que ha tingut cada empleat. Si l’empleat no ha tingut cap treure el camp “historial_feines”.
   ```js

   ```

8. Com que tot empleat té una feina incorpora la feina actual com una feina més.
   ```js

   ```

9. Mostra aquells empleats que han tingut 2 feines o més.
   ```js

   ```

10.Per cada empleat mostra les dades del seu departament. Redefineix el mateix camp departament del document empleats.
   ```js

   ```

11.Si has utilitzat $join a l’exercici anterior veuràs que el camp departament és un array. Per tant fés el que necessitis perquè aquest camp sigui un objecte a on hi
hagi la informació del departament i no un array.
   ```js

   ```
