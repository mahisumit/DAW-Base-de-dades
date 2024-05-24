# Exercici 0 – Importació de la BD #

Importa els fitxers .json per la BD de [rrhh:](https://github.com/mahisumit/DAW-BaseDeDades/blob/main/4.%20Base%20de%20dades%20objecte%20relacionals%20(UF4)/DataBase/rrhh.zip). <br>
Passos: <br>
• Crea la BD [rrhh](https://github.com/mahisumit/DAW-BaseDeDades/blob/main/4.%20Base%20de%20dades%20objecte%20relacionals%20(UF4)/DataBase/rrhh.zip) <br>
• Importa el fitxer departaments.json → col·lecció departaments <br>
• Importa el fitxer empleats.json → col·lecció empleats

## Exercicis CONSULTA ##

1. Obtenir de tots els empleats, el nom, cognoms i salari. Mostrar només 4 registres.
```js
db.empleats.find({}, {nom: 1, cognoms: 1, salari: 1, _id: 0}).limit(4)
```

2. Mostra la quantitat de departaments que hi ha.
```js
db.departaments.count()
```

3. Recupera l’empleat “emplat_id=100”.
```js
db.empleats.find({emplat_id: 100})
```

4. Recupera els empleats amb el càrrec de “President”.
```js
db.empleats.find({"feina.nom":"President"},{})
```

5. Recupera els empleats que treballen al departament de “IT”.
```js
db.empleats.find({"departament.nom":"IT"},{})
```

6. Recupera els empleats que van ser contractats a partir de l’1 de gener de 1985.
```js
db.empleats.find({data_contractacio:{$gte:new Date("1985-01-01")}},{})
```

7. Recupera els empleats amb un salari superior a 2000.
```js
db.empleats.find({salari:{$gt:2000}},{})
```

8. Recupera els empleats amb un salari entre 2000 i 6000.
```js
db.empleats.find({$and:[{salari:{$gte:2000}}, {salari:{$lte:6000}}]},{})
```

9. Recupera els empleats que el seu número de telèfon comença per 515.
```js
db.empleats.find({"telefon":{$regex: /^515/}},{})
```

10. Recupera els empleats que no treballin de Vice President. Utilitza el codi de la feina.
"AD_VP"
```js
db.empleats.find({"feina.codi": {$ne:"AD_VP"}},{})
```

11. Recupera els empleats que tenen pct_comissio.
```js
db.empleats.find({pct_comissio: {$exists:true}},{})
```

12. Recupera els empleats que tenen pct_comissio i hagi treballat o treballin actualment de "Cap de Vendes" . Utilitza el codi de feina "SA_MAN".
```js
db.empleats.find({$and: [{pct_comissio: {$exists:true}}, {$or: [{"feina.codi": "SA_MAN"},{"historial_feines.feina.codi": "SA_MAN"}]}]},{})
```
13. Recupera els empleats que han tingut 2 feines. No tinguis en compte la feina actual.
```js
db.empleats.find({historial_feines: {$size:2}},{})
```
## Exercicis INSERT / UPDATE / DELETE ##

1. Afegeix-te com empleat del departament d’Administració. Com a historial feines has treballat del 01/01/2000 al 31/12/2000 de “Contable” (AC_ACCOUNT) i del
01/01/2001 al 31/12/2002 com a “Ajudant de direcció”( AD_ASST).
Inventa’t les dades que creguis convenients.
```js

```

2. Afegeix un Departament anomenat “Control de Qualitat amb codi” 120. Aquest Departament té la mateixa localització que el departament de Recursos Humans (190).
```js

```

3. Modifica l’empelat anterior per tal de que treballi en el departament de “Control de Qualitat” (120).
```js

```

4. 4. Afegeix un historial_feines per l'empleat amb codi empleat_id = 100. Amb el
següents valors: <br>
{<br>
  &nbsp;&nbsp;&nbsp;"data inici": 01/01/2010,<br>
  &nbsp;&nbsp;&nbsp;"data fi" :05/05/2010,<br>
  &nbsp;&nbsp;&nbsp;"feina" : {<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"codi" : "SA MAN",<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"nom" : "Cap logística"<br>
}<br>
  &nbsp;&nbsp;&nbsp;"departament" : {<br>
  &nbsp;&nbsp;&nbsp;"codi" :90,<br>
  &nbsp;&nbsp;&nbsp;"nom" : "Direcció"<br>
 &nbsp;&nbsp; }<br>
}<br>
```js

```

5 .Esborra tots els empleats que siguin del departament amb codi 10.
```js

```
