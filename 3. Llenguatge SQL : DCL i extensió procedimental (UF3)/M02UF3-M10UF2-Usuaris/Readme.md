# Crear Usuaris i Premisos

1. Crear l'ususari 1.
```sql
CREATE USER 'elon'@'localhost' IDENTIFIED BY 'password';
```

2. Crear l'usuari 2.
```sql
CREATE USER 'mahi'@'localhost' IDENTIFIED BY 'password';
```

3. Ususari 1 quan es connecti desde la pròpia màquina que pugui crear, I,U,D,S de tots els objects. 
```sql
GRANT INSERT,UPDATE,DELETE,SELECT ON rrhh.* TO 'elon'@'localhost';
```

4. USUARI 2 quan es connecti de de la pròpia màquina que pugui fer: 
	SELECT totes les taules.
    UPDATE de la columna salari de la taula empleats de la BD rrhh.
```sql
GRANT SELECT ON rrhh.* TO 'mahi'@'localhost';
GRANT UPDATE (salari) ON rrhh.empleats TO 'mahi'@'localhost';
```

5. Usuari 1 quan es connecti des de qualsevol màquina que mómes pugui fer SELECT de la BD rrhh. 
```sql
GRANT SELECT ON rrhh.* TO'elon'@'%';
```

6. Per veure els premisos del usuari.
```sql
SHOW GRANTS FOR 'elon'@'localhost'; 
```