# Activitat DML

## DML (INSERT, UPDATE, DELETE)

**Exercici 1**

```mysql
INSERT INTO empleats (empleat_id, nom, cognoms, email, data_contractacio, feina_codi, salari)
VALUES ('208', 'Pere', 'Pi', 'perepi@empresa.cat', '1995-08-18', 'IT_PROG','7000');
```

**Exercici 2**

```mysql
INSERT INTO empleats (empleat_id, nom, cognoms, email, data_contractacio, feina_codi, salari)
VALUES 	('209', 'Sandra', 'González', 'sgonzález@empresa.cat', '1995-08-19', 'AC_ACCOUNT','6000'),
	('210', 'Marta', 'Pérez', 'mperez@empresa.cat', '1995-08-20', 'AC_ACCOUNT','6000'),
        ('2011', 'Maria', 'Cantó', 'mcanto@empresa.cat', '1995-08-21', 'AC_ACCOUNT','6000');
```

**Exercici 3**

```mysql
INSERT INTO empleats (empleat_id, nom, cognoms, email, data_contractacio, feina_codi, salari)
VALUES 	('212', 'Pau', 'Serra', 'pserra@empresa.cat', '1995-08-20', 'IT_PROG', '1000');

INSERT INTO historial_feines (empleat_id, data_inici, data_fi, feina_codi, departament_id)
VALUES 	('212', '1992-01-15', '1993-10-20', 'IT_PROG', '60'),
	('212', '1993-10-21', '1994-10-21', 'SA_MAN', '90'),
	('212', '1994-10-21', '1994-12-31', 'MK_MAN', '20');
```

**Exercici 4**

```mysql
INSERT INTO paisos (pais_id, nom, regio_id)
VALUES	('ES', 'Espanya','1'),
	('FR', 'França', '1'),
        ('AU', 'Austràlia', '1'),
        ('JP', 'Japó', '2'),
        ('KR', 'Corea del Sud', '2');
```

**Exercici 5**

```mysql
UPDATE localitzacions
SET adreca = 'Sa Palomera' 
WHERE adreca = '460 Bloor St. W.' AND ciutat = 'Toronto';
```

**Exercici 6**

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

**Exercici 7**

```mysql
DELETE FROM historial_feines
	WHERE empleat_id = '101'
  AND data_inici = '1993-09-21'
  AND data_fi = '1993-10-27';
```

***

## DML (CONSULTES)

**Exercici 8**

```mysql
DESCRIBE empleats;
```

**Exercici 9**

```mysql
SELECT	nom,
		cognoms,
    salari
	FROM empleats
    LIMIT 4;
```
**Exercici 10**

```mysql
SELECT * FROM feines;
```

**Exercici 11**

```mysql

```
**Exercici 12**

```mysql

```

**Exercici 13**

```mysql

```
**Exercici 14**

```mysql

```

**Exercici 15**

```mysql

```
