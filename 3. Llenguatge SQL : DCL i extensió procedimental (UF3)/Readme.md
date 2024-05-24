# UF 3

***

## Data Control Language (DCL):
DCL s'utilitza per controlar l'accés als dades dins de la base de dades. Les comandes DCL gestionen els permisos i la seguretat de la base de dades.

***

### Comandes principals de DCL:

* GRANT: Atorga permisos a usuaris o rols per realitzar operacions específiques en la base de dades.
```sql
GRANT SELECT, INSERT ON Employees TO User1;
```

* REVOKE: Revoca permisos atorgats anteriorment a usuaris o rols.
```sql
REVOKE INSERT ON Employees FROM User1;
```

***

## Extensió procedimental en SQL:
A més de les comandes bàsiques d'SQL, molts sistemes de bases de dades ofereixen extensions procedimentals que permeten escriure codi més complex per gestionar la lògica de la base de dades. Això inclou la capacitat de definir funcions, procediments emmagatzemats, i desencadenadors (triggers).

***

### Elements principals de les extensions procedimentals:

* Procediments emmagatzemats: Són col·leccions de sentències SQL que s'emmagatzemen a la base de dades i es poden executar com una unitat.
```sql
çCREATE PROCEDURE AddEmployee (
    IN p_FirstName VARCHAR(50),
    IN p_LastName VARCHAR(50),
    IN p_BirthDate DATE,
    IN p_Position VARCHAR(50)
)
BEGIN
    INSERT INTO Employees (FirstName, LastName, BirthDate, Position)
    VALUES (p_FirstName, p_LastName, p_BirthDate, p_Position);
END;
```

* Funcions: Són similars als procediments emmagatzemats, però poden retornar un valor.
```sql
CREATE FUNCTION GetEmployeeFullName (EmployeeID INT)
RETURNS VARCHAR(100)
BEGIN
    DECLARE FullName VARCHAR(100);
    SELECT CONCAT(FirstName, ' ', LastName) INTO FullName
    FROM Employees
    WHERE EmployeeID = EmployeeID;
    RETURN FullName;
END;
```

* Triggers: Són procediments automàtics que s'executen en resposta a certs esdeveniments en una taula, com insercions, actualitzacions o eliminacions.
```sql
DELIMITER //
CREATE TRIGGER trg_ActualitzaSaldos BEFORE INSERT
ON t1 FOR EACH ROW
BEGIN
 INSERT INTO t1 (c1) VALUES(NEW.c1);
END//
INSERT INTO t1 (c1) VALUES(1);
```

* Cursors: S'utilitzen per manipular un conjunt de files en una base de dades de manera controlada.
```sql
DECLARE cursor1 CURSOR FOR
SELECT EmployeeID, FirstName, LastName FROM Employees;

OPEN cursor1;
FETCH cursor1 INTO @EmployeeID, @FirstName, @LastName;
CLOSE cursor1;
```

***

## Exemples concrets:

* Grant permissions (DCL):
```sql
GRANT UPDATE ON Products TO User2;
```

* Revoke permissions (DCL)
```sql
REVOKE UPDATE ON Products FROM User2;
```

* Crear un procediment emmagatzemat (Extensió procedimental)
```sql
CREATE PROCEDURE UpdateProductStock (
    IN p_ProductID INT,
    IN p_NewStock INT
)
BEGIN
    UPDATE Products
    SET Stock = p_NewStock
    WHERE ProductID = p_ProductID;
END;
```

* Crear una funció (Extensió procedimental)
```sql
CREATE FUNCTION GetProductPrice (p_ProductID INT)
RETURNS DECIMAL(10, 2)
BEGIN
    DECLARE Price DECIMAL(10, 2);
    SELECT Price INTO Price
    FROM Products
    WHERE ProductID = p_ProductID;
    RETURN Price;
END;
```

* Crear un trigger (Extensió procedimental)
```sql
CREATE TRIGGER UpdateProductLog
AFTER UPDATE ON Products
FOR EACH ROW
BEGIN
    INSERT INTO ProductLog (ProductID, OldPrice, NewPrice, ChangeDate)
    VALUES (OLD.ProductID, OLD.Price, NEW.Price, NOW());
END;
```
