# Activitat DML

## DML (INSERT, UPDATE, DELETE)

### **Exercici 1 - DML (INSERT, UPDATE, DELETE)**
Exercici 1 - Afegeix a la BD un empleat anomenat Pere Pi que treballa com a
programador amb un salari 7.000€.

```mysql
INSERT INTO empleats (empleat_id, nom, cognoms, email, data_contractacio, feina_codi, salari)
VALUES ('208', 'Pere', 'Pi', 'perepi@empresa.cat', '1995-08-18', 'IT_PROG','7000');
```

### **Exercici 2 - DML (INSERT, UPDATE, DELETE)**
Exercici 2 - Afegeix amb una sola sentència DML 3 empleades (Sandra González, Marta
Pérez i Maria Cantó) que treballen com a contables amb el mateix salari de 6.000€ .

```mysql
INSERT INTO empleats (empleat_id, nom, cognoms, email, data_contractacio, feina_codi, salari)
VALUES 	('209', 'Sandra', 'González', 'sgonzález@empresa.cat', '1995-08-19', 'AC_ACCOUNT','6000'),
	('210', 'Marta', 'Pérez', 'mperez@empresa.cat', '1995-08-20', 'AC_ACCOUNT','6000'),
        ('2011', 'Maria', 'Cantó', 'mcanto@empresa.cat', '1995-08-21', 'AC_ACCOUNT','6000');
```

### **Exercici 3 - DML (INSERT, UPDATE, DELETE)**
Exercici 3 - Afegeix a la BD un empleat anomenat Pau Serra amb el següent historial
laboral:
- 15 de Gener del 1992 al 20 d'Octubre del 1993 va fer de programador en el
departament d'informàtica (IT).
- 21 d'Octubre del 1993 al 21 d'Octubre del 1994 va fer de venedor pel
departament de vendes.
- 21 d'Octubre del 1994 al 31 de desembre del 1994 va fer de cap de vendes dins
assignat en el departament de vendes.

```mysql
INSERT INTO empleats (empleat_id, nom, cognoms, email, data_contractacio, feina_codi, salari)
VALUES 	('212', 'Pau', 'Serra', 'pserra@empresa.cat', '1995-08-20', 'IT_PROG', '1000');

INSERT INTO historial_feines (empleat_id, data_inici, data_fi, feina_codi, departament_id)
VALUES 	('212', '1992-01-15', '1993-10-20', 'IT_PROG', '60'),
	('212', '1993-10-21', '1994-10-21', 'SA_MAN', '90'),
	('212', '1994-10-21', '1994-12-31', 'MK_MAN', '20');
```

### **Exercici 4 - DML (INSERT, UPDATE, DELETE)**
Exercici 4 - Afegeix els següents països: Espanya, França, Austràlia, Japó i Corea del
Sud. Tenint en compte que els codis de país segueixen l'ISO internacional en el camp
pais_id.

```mysql
INSERT INTO paisos (pais_id, nom, regio_id)
VALUES	('ES', 'Espanya','1'),
	('FR', 'França', '1'),
        ('AU', 'Austràlia', '1'),
        ('JP', 'Japó', '2'),
        ('KR', 'Corea del Sud', '2');
```

### **Exercici 5 - DML (INSERT, UPDATE, DELETE)**
Exercici 5 - Modifica l'adreça 460 Bloor St. W. de Toronto per l'adreça del teu centre.

```mysql
UPDATE localitzacions
SET adreca = 'Sa Palomera' 
WHERE adreca = '460 Bloor St. W.' AND ciutat = 'Toronto';
```

### **Exercici 6 - DML (INSERT, UPDATE, DELETE)**
Exercici 6 - Quines sentència o sentències utilitzaries per modificar tots els empleats
que són presidents (President) passin a ser Vicepresidents d'administració
(Administration Vice President) i al revés tots els Vicepresidents d'administració passin a
ser presidents.

```mysql
UPDATE empleats
	SET feina_codi = "TMP"
WHERE feina_codi = "AD_PRES";

UPDATE empleats
	SET feina_codi = "AD_PRES"
WHERE feina_codi = "AD_VP";

UPDATE empleats
	SET feina_codi = "AD_VP"
WHERE feina_codi = "TMP";

DELETE FROM feines WHERE feina_codi = "TMP";
```

### **Exercici 7 - DML (INSERT, UPDATE, DELETE)**
Exercici 7 - Quina sentència DML utilitzaries per esborrar tot l'historial de treball d'un
empleat concret entre dues dates. Posa'n un exemple.

```mysql
DELETE FROM historial_feines
	WHERE empleat_id = '101'
  AND data_inici = '1993-09-21'
  AND data_fi = '1993-10-27';
```

***

## DML (CONSULTES)

### **Exercici 8 - DML (CONSULTES)**
Exercici 8 - Mostrar l’estructura de la taula empleats.

```mysql
DESCRIBE empleats;
```

### **Exercici 9 - DML (CONSULTES)**
Exercici 9 - Obtenir de tots els empleats, el nom, cognoms i salari. Mostrar només 4
registres.

```mysql
SELECT	nom,
	cognoms,
    	salari
	FROM empleats
    LIMIT 4;
```
### **Exercici 10  - DML (CONSULTES)**
Exercici 10 - Obtenir tots els treballs ( totes les columnes ).

```mysql
SELECT * FROM feines;
```

### **Exercici 11 - DML (CONSULTES)**
Exercici 11 - Obtenir els diferents codis de departaments dels empleats, sense duplicats.

```mysql
SELECT DISTINCT departament_id
FROM empleats
WHERE departament_id IS NOT NULL;
```
### **Exercici 12 - DML (CONSULTES)**
Exercici 12 - Volem saber de tots els empleats, el codi d’empleat (pk), els cognoms i
nom , el salari i el salari en pessetes (SalariPTS).

```mysql
SELECT empleat_id, cognoms, nom, salari, salari * 166.386 AS SalariPTS
	FROM empleats;
```

### **Exercici 13 - DML (CONSULTES)**
Exercici 13 - Mostrar el cognom, nom i salari dels empleats que guanyen més de 12000.

```mysql
SELECT cognoms, nom, salari
	FROM empleats 
WHERE salari >12000;
```
### **Exercici 14 - DML (CONSULTES)**
Exercici 14 - Mostra tota la informació dels països ordenada per nom de país.

```mysql
SELECT *
	 FROM paisos
ORDER BY nom;
```

### **Exercici 15 - DML (CONSULTES)**
Exercici 15 - Mostrar el nom dels països amb codi de regió 2.

```mysql
SELECT *
	FROM paisos
WHERE regio_id = 2;
```

### **Exercici 16 - DML (CONSULTES)**
Exercici 16 - Volem saber el cognom, codi de departament i email de l’empleat 176.

```mysql
SELECT *
	FROM empleats
WHERE empleat_id = 176;
```
### **Exercici 17 - DML (CONSULTES)**
Exercici 17 - Mostra totes les dades dels empleats contractats a partir del 1996.

```mysql
SELECT cognoms, email, departament_id
	FROM empleats
WHERE data_contractacio>='1996-01-01';alter
```
