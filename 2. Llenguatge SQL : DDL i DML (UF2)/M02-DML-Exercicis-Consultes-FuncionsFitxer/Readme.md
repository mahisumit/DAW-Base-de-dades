# DML (CONSULTES AMB FUNCIONS)

### **Exercici 1 - DML (CONSULTES AMB FUNCIONS)**
Exercici 1 - Escriu una consulta per mostrar la data actual. Anomena la columna com a“Data”.

```mysql
SELECT CURRENT_DATE AS "Data";
```
### **Exercici 2 - DML (CONSULTES AMB FUNCIONS)**
Exercici 2 - Escriu una consulta per mostrar la data i hora actual. Anomena la columna com a “Data Hora”.

```mysql
SELECT CURRENT_DATE, CURRENT_TIME AS "Data Hora";
SELECT NOW() AS "Data Hora";
```
### **Exercici 3 - DML (CONSULTES AMB FUNCIONS)**
Exercici 3 - Mostra els cognoms i nom dels empleats concatenats amb una coma i un espai en blanc.

```mysql
SELECT CONCAT (cognoms, ', ', nom)
	FROM empleats;
```
### **Exercici 4 - DML (CONSULTES AMB FUNCIONS)**
Exercici 4 - Volem una columna on estigui tot en majúscules i l’altre tot en minúscules. Anomena les columnes com a “Nom en majúscules” i “Nom en minúscules” respectivament.

```mysql
SELECT 	UPPER  (nom) AS 'NOM en majúscules',
		LOWER  (nom) AS 'NOM en minúscules'
FROM empleats;
```
### **Exercici 5 - DML (CONSULTES AMB FUNCIONS)**
Exercici 5 - Mostra les 6 primeres lletres dels cognoms dels empleats.

```mysql
SELECT LEFT(cognoms,6)
	FROM empleats;
```
### **Exercici 6 - DML (CONSULTES AMB FUNCIONS)**
Exercici 6 - Quins són els empleats que tenen la longitud del cognom major a 6? ( Mostra el cognom i la longitud ).

```mysql
SELECT cognoms, LENGTH(cognoms) AS longitud
	FROM empleats
WHERE LENGTH (cognoms) >6;
```
### **Exercici 7 - DML (CONSULTES AMB FUNCIONS)**
Exercici 7 - Substitueix totes les ‘a’ dels cognoms dels empleats per ’e’. Ordena pel nouvalor del cognom.

```mysql
SELECT cognoms,REPLACE(REPLACE(cognoms, 'a', 'e'),'A','E') AS cognoms_n
	FROM empleats;
```
### **Exercici 8 - DML (CONSULTES AMB FUNCIONS)**
Exercici 8 -  Mostra tots els empleats que tenen en la segona posició del cognom una ‘a’. ( Sense utilitzar l’operador LIKE, ni REGEXP).

```mysql
SELECT cognoms
FROM empleats
WHERE UPPER(SUBSTRING(cognoms, 2, 1)) = 'A';
```
### **Exercici 9 - DML (CONSULTES AMB FUNCIONS)**
Exercici 9 - Per cada empleat mostra el codi d’empleat, cognom i el salari amb un augment del 15% expressat com un número enter, etiqueta la columna amb el nom “NouSalari”.

```mysql
SELECT salari,
	ROUND(salari * 1.15,0) AS NouSalari
FROM empleats;
```
### **Exercici 10 - DML (CONSULTES AMB FUNCIONS)**
Exercici 10 - Partint de la consulta anterior, afegeix una nova columna que mostri la diferencia salarial entre el nou salari i l’antic. Etiqueta la columna com a “Increment”.

```mysql
SELECT salari,
	ROUND(salari * 1.15,0) AS NouSalari,
        ROUND(ROUND(salari * 1.15,0) - salari,0) AS Increment 
FROM empleats;
```
### **Exercici 11 - DML (CONSULTES AMB FUNCIONS)**
Exercici 11 - Fes una consulta on mostri el cognom de l’empleat en majúscules i la longitud del cognom dels empleats on el seu cognom comenci per J, A o M. Ordena els resultats per cognom d’empleat.

```mysql
SELECT UPPER (cognoms), LENGTH (cognoms)
	FROM empleats 
WHERE cognoms LIKE 'j%'
	OR cognoms LIKE 'A%'
    	OR cognoms LIKE 'M%';
```
### **Exercici 12 - DML (CONSULTES AMB FUNCIONS)**
Exercici 12 - Mostra l’import de comissió dels empleats. Etiqueta la columna com a “ImportCommissio” i arrodoneix el valor a 2 decimals. Si un empleat no té assignada comissió fes el que calgui per tal que el resultat de l’operació surti zero en comptes de NULL. Mostra també el cognom i el salari en Ptes despreciant els decimals ( truncar ).

```mysql
SELECT ROUND(IFNULL(pct_comissio,0),2) AS ImportComissio,
	cognoms,
        TRUNCATE(salari * 166.386,0)
FROM empleats;
```
### **Exercici 13 - DML (CONSULTES AMB FUNCIONS)**
Exercici 13 - Utilitzant alguna de les funcions de dates, obté el nom, cognom i data de contractació dels empleats contractats durant el 1997.

```mysql
SELECT nom, cognoms, data_contractacio
	FROM empleats
WHERE YEAR(data_contractacio) = 1997
AND data_contractacio BETWEEN '1997-01-01' AND '1997-12-31';
```
### **Exercici 14 - DML (CONSULTES AMB FUNCIONS)**
Exercici 14 - Utilitzant alguna de les funcions de data, mostra tots els empleats que van ser contractats entre els mesos de juny i novembre, independentment de l’any.

```mysql
SELECT nom, cognoms, data_contractacio
	FROM empleats 
WHERE (MONTH(data_contractacio) BETWEEN 6 AND 11)
	OR (MONTH(data_contractacio) = 1)
AND data_contractacio Between '1997-01-01' AND '1997-12-31';
```
### **Exercici 15 - DML (CONSULTES AMB FUNCIONS)**
Exercici 15 - El nostre departament de recursos humans s’aborreix molt i per justificar el seu sou està elaborant tot d’estadístiques extranyes. Ara volen saber quins empleats varen ser contractats en un dia parell. 

```mysql
SELECT *
	FROM empleats
WHERE DAYOFMONTH(data_contractacio) % 2 = 0;
```
### **Exercici 16 - DML (CONSULTES AMB FUNCIONS)**
Exercici 16 - 

```mysql
SELECT DATE_FORMAT(data_contractacio, "%Y-%m")
	FROM empleats;
```
### **Exercici 17 - DML (CONSULTES AMB FUNCIONS)**
Exercici 17 - Mostra el codi d’empleat, cognom i la data de contractació en format AAAAMM. El dia no ens interessa ara en el nostre estudi estadístic. Ordena per aquest nou format de data.

```mysql
SELECT empleat_id, cognoms, DATE_FORMAT(data_contractacio, '%Y%m') AS data_contractacio
	FROM empleats
ORDER BY data_contractacio;
```
### **Exercici 18 - DML (CONSULTES AMB FUNCIONS)**
Exercici 18 - Si sumem 234 dies a la data d’avui a quin dia estarem?

```mysql
SELECT DATE_ADD(CURDATE(),INTERVAL 234 DAY);
```
### **Exercici 19 - DML (CONSULTES AMB FUNCIONS)**
Exercici 19 -  I si sumem 12 hores?

```mysql
SELECT DATE_ADD(NOW(),INTERVAL 12 HOUR);
```
### **Exercici 20 - DML (CONSULTES AMB FUNCIONS)**
Exercici 20 - Per cada empleat, mostra el cognom, la data de contractació i el número de mesos entre el dia d’avui i la data de contractació. Etiqueta la columna com a “MesosTreballats” i redondeja sense decimals. Ordena el resultat segons els mesos treballats de més a menys.

```mysql
SELECT data_contractacio,TIMESTAMPDIFF(YEAR,data_contractacio,curdate())
	FROM empleats;
```
### **Exercici 21 - DML (CONSULTES AMB FUNCIONS)**
Exercici 21 - Mostra el nom, cognom i anys d’antiguitat dels empleats que tenen una antiguitat superior o igual a 20 anys a l’empresa.

```mysql
SELECT *
	FROM empleats
WHERE TIMESTAMPDIFF(YEAR,data_contractacio,curdate())>=20;
```
### **Exercici 22 - DML (CONSULTES AMB FUNCIONS)**
Exercici 22 - Crea una consulta per mostrar el cognom i salari de tots els empleats que guanyen més de 10.000 a l’any. Dona format al camp salari per a que tingui 15 caràcters de longitud, omplint per l’esquerra amb $. Etiqueta la columna com a salari.

```mysql
SELECT salari, LPAD(salari,15,'$')
	FROM empleats
WHERE salari > 10000;
```
### **Exercici 23 - DML (CONSULTES AMB FUNCIONS)**
Exercici 23 - Mostra el cognom, salari i percentatge de comissió dels empleats. Afegeix una nova columna en que si un empleat no té assignada comissió, posi “Sense Comissio”. Etiqueta la columna amb nom “NoComissio”

```mysql
SELECT salari, IFNULL(pct_comissio,"SENSE Comissio")
	FROM empleats;
```
### **Exercici 24 - DML (CONSULTES AMB FUNCIONS)**
Exercici 24 - Mostra el cognom, salari i utilitzant la funció CASE, mostra el següent en funció del valor del salari:
- Si el salari està entre 0 i 3000 -> “Mig”
- Si el salari està entre 12000 i 24000 -> “Alt”
- Qualsevol altre valor posa “Altres”
- Anomena la columna com a “PoderAdquisitiu” i ordena per salari de menor a major.

```mysql
SELECT salari,
	CASE
	When salari BETWEEN 0 AND 3000 THEN "MIG"
        WHEN salari BETWEEN 12000 AND 24000 THEN "ALT"
        ELSE "ALTRES"
END AS "PoderAdquistiu"
	FROM empleats
ORDER BY salari ASC;
```
