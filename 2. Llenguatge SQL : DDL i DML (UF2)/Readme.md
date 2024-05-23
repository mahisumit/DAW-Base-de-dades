# UF 2

***

## DDL, DML 

***

### Data Definition Language (DDL): 
DDL s'utilitza per definir i modificar l'estructura de la base de dades, incloent-hi la creació, modificació i eliminació de taules i altres objectes de la base de dades.

#### Comandes principals de DDL:

* CREATE: Crea una nova taula, vista, índex o altres objectes de base de dades.
```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    BirthDate DATE,
    Position VARCHAR(50)
);
```

* ALTER: Modifica l'estructura d'una taula existent, com afegir, eliminar o modificar columnes.

```sql
ALTER TABLE Employees ADD Email VARCHAR(100);
```

* DROP: Elimina una taula, vista, índex o altres objectes de base de dades.

```sql
DROP TABLE Employees;
```

* TRUNCATE: Elimina totes les files d'una taula sense eliminar l'estructura de la taula.
```sql
TRUNCATE TABLE Employees;
```

***

### Data Manipulation Language (DML):
DML s'utilitza per manipular les dades emmagatzemades dins de les taules. Aquest llenguatge inclou operacions per inserir, actualitzar, eliminar i consultar dades.

#### Comandes principals de DML:

* INSERT: Insereix noves files en una taula.
```sql
INSERT INTO Employees (EmployeeID, FirstName, LastName, BirthDate, Position)
VALUES (1, 'John', 'Doe', '1980-01-01', 'Manager');
```

* UPDATE: Actualitza les dades existents en una taula.
```sql
UPDATE Employees
SET Position = 'Senior Manager'
WHERE EmployeeID = 1;
```

DELETE: Elimina files d'una taula.
```sql
DELETE FROM Employees
WHERE EmployeeID = 1;
```

SELECT: Consulta dades d'una o més taules.
```sql
SELECT FirstName, LastName, Position
FROM Employees
WHERE Position = 'Manager';
```

***

