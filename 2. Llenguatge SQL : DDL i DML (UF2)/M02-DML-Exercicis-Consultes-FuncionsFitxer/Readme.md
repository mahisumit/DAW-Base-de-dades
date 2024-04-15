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
Exercici 6 - 

```mysql

```
### **Exercici 7 - DML (CONSULTES AMB FUNCIONS)**
Exercici 7 - 

```mysql

```
### **Exercici 8 - DML (CONSULTES AMB FUNCIONS)**
Exercici 8 - 

```mysql

```
### **Exercici 9 - DML (CONSULTES AMB FUNCIONS)**
Exercici 9 - 

```mysql

```
### **Exercici 10 - DML (CONSULTES AMB FUNCIONS)**
Exercici 10 - 

```mysql

```
### **Exercici 11 - DML (CONSULTES AMB FUNCIONS)**
Exercici 11 - 

```mysql

```
### **Exercici 12 - DML (CONSULTES AMB FUNCIONS)**
Exercici 12 - 

```mysql

```
### **Exercici 13 - DML (CONSULTES AMB FUNCIONS)**
Exercici 13 - 

```mysql

```
### **Exercici 14 - DML (CONSULTES AMB FUNCIONS)**
Exercici 14 - 

```mysql

```
### **Exercici 15 - DML (CONSULTES AMB FUNCIONS)**
Exercici 15 - 

```mysql

```
### **Exercici 16 - DML (CONSULTES AMB FUNCIONS)**
Exercici 16 - 

```mysql

```
### **Exercici 17 - DML (CONSULTES AMB FUNCIONS)**
Exercici 17 - 

```mysql

```
### **Exercici 18 - DML (CONSULTES AMB FUNCIONS)**
Exercici 18 - 

```mysql

```
### **Exercici 19 - DML (CONSULTES AMB FUNCIONS)**
Exercici 19 - 

```mysql

```
### **Exercici 20 - DML (CONSULTES AMB FUNCIONS)**
Exercici 20 - 

```mysql

```
### **Exercici 21 - DML (CONSULTES AMB FUNCIONS)**
Exercici 21 - 

```mysql

```
### **Exercici 22 - DML (CONSULTES AMB FUNCIONS)**
Exercici 22 - 

```mysql

```
### **Exercici 23 - DML (CONSULTES AMB FUNCIONS)**
Exercici 23 - 

```mysql

```
### **Exercici 24 - DML (CONSULTES AMB FUNCIONS)**
Exercici 24 - 

```mysql

```
