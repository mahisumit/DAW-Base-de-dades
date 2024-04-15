# DML (CONSULTES D’AGRUPAMENT)

### **Exercici 1 - DML (CONSULTES D’AGRUPAMENT)**
Exercici 1 - Quants empleats van ser contractats l'any passat.

```mysql
SELECT COUNT(*) AS "Empleats Contracts Enguany"
	FROM empleats
WHERE DATE_FORMAT(data_contractacio, "%Y") = YEAR(CURDATE())-1 ;
```
### **Exercici 2 - DML (CONSULTES D’AGRUPAMENT)**
Exercici 2 - Quin és el treballador (nº d’anys no el nom del treballador) amb més anys d'antiguitat?

```mysql
SELECT TIMESTAMPDIFF(Year, Min(data_contractacio),CURDATE())
	FROM empleats;
```
### **Exercici 3 - DML (CONSULTES D’AGRUPAMENT)**
Exercici 3 - Quin és el treballador(nº d’anys no el nom del treballador) amb menys anys d'antiguitat?

```mysql
SELECT TIMESTAMPDIFF(Year, Max(data_contractacio),CURDATE())
	FROM empleats;
```
### **Exercici 4 - DML (CONSULTES D’AGRUPAMENT)**
Exercici 4 - Quin és el salari mig de l'empresa?

```mysql
SELECT AVG(salari) AS salari_mig
	FROM empleats;
```
### **Exercici 5 - DML (CONSULTES D’AGRUPAMENT)**
Exercici 5 - Mostra el salari més alt i el més baix dels empleats. Anomena les columnes com a salari_max i salari_min respectivament.

```mysql
SELECT	MAX(salari) AS salari_max,
		MIN(salari) AS salari_min,
		AVG(salari)
	FROM empleats
```
### **Exercici 6 - DML (CONSULTES D’AGRUPAMENT)**
Exercici 6 -  Mostra la mitjana dels salaris i el número d’empleats que tenim. Arrodoneix la mitjana al número enter més pròxim i anomena les columnes com a salari_mig i num_empleats respectivament.

```mysql
SELECT round(AVG(salari),0)
	FROM empleats;
```
### **Exercici 7 - DML (CONSULTES D’AGRUPAMENT)**
Exercici 7 - Mostra, per cada tipus de treball, la mitjana dels salaris. Ordena la informació per tipus de treball.

```mysql
SELECT feina_codi,AVG(salari)
	FROM empleats 
GROUP BY feina_codi
ORDER BY feina_codi;
```
### **Exercici 8 - DML (CONSULTES D’AGRUPAMENT)**
Exercici 8 - Quants empleats tenim assignats a cada tipus de treball? Ordena lainformació per número d’empleats.

```mysql
SELECT departament_id,COUNT(*)
	FROM empleats 
WHERE departAment_id IS NOT NULL
GROUP BY departament_id;
```
### **Exercici 9 - DML (CONSULTES D’AGRUPAMENT)**
Exercici 9 -  Quants empleats tenim assignats a cada departament? Mostra el codi de departament i el número d’empleats que té. Ordena la informació per número d’empleats.

```mysql
SELECT departament_id, COUNT(*) AS nombre_empleats
  FROM empleats
GROUP BY departament_id
ORDER BY nombre_empleats DESC;
```
### **Exercici 10 - DML (CONSULTES D’AGRUPAMENT)**
Exercici 10 - Partint de la consulta anterior, volem saber també quants empleats no tenen departament assignat. Mostra el text “No assignat” com a identificador del departament.

```mysql
SELECT IFNULL(departament_id,"No assignat") AS departament_id,COUNT(*)
	FROM empleats
GROUP BY departament_id;
```
### **Exercici 11 - DML (CONSULTES D’AGRUPAMENT)**
Exercici 11 - Quants directors (caps) diferents tenim? Anomena la columna com a numero_de_directors.

```mysql
SELECT COUNT(DISTINCT id_cap) AS "Numero de directors"
	FROM empleats;
```
### **Exercici 12 - DML (CONSULTES D’AGRUPAMENT)**
Exercici 12 - Fes una consulta per calcular la diferència que hi ha entre el salari major i el menor dels empleats. Anomena la columna com a Diferencia.

```mysql
SELECT (MAX(salari) - MIN(salari)) AS Diferencia
  FROM empleats;
```

### **Exercici 13 - DML (CONSULTES D’AGRUPAMENT)**
Exercici 13 - Mostra, per cada cap, el número identificador de l’empleat (com a cap) i el salari de l’empleat pitjor pagat per a aquest cap. Exclou els empleats que no tinguin assignat cap.

```mysql
SELECT id_cap, MIN(salari)
	FROM empleats
WHERE id_cap IS NOT NULL
GROUP BY id_cap;
```
### **Exercici 14 - DML (CONSULTES D’AGRUPAMENT)**
Exercici 14 - Partint de la consulta anterior, exclou també aquells caps en què el salari mínim sigui inferior o igual a 6.000.

```mysql
SELECT (MAX(salari) - MIN(salari)) AS Diferencia
  FROM empleats
WHERE empleat_id NOT IN (SELECT id_cap
                            FROM departaments
                            WHERE salari <= 6000);
```
### **Exercici 15 - DML (CONSULTES D’AGRUPAMENT)**
Exercici 15 - Obté el número d’empleats contractats per cada any. Ordena la informació per any.

```mysql
SELECT YEAR(data_contractacio)any, COUNT(*)
	FROM empleats
GROUP BY YEAR(data_contractacio)
ORDER BY any; 
```
