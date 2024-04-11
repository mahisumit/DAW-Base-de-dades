# Activitat Subprogrames

## Enunciat de Funcions 

**Exercici 1**

```mysql
DELIMITER //
DROP FUNCTION IF EXISTS sp_Data //
CREATE FUNCTION sp_Data(p_dataOrigen DATE) RETURNS VARCHAR(10) DETERMINISTIC
BEGIN
    DECLARE v_dataFinal VARCHAR(10);
    
    SET v_dataFinal = DATE_FORMAT(p_dataOrigen, '%d-%m-%Y');
    
    RETURN v_dataFinal;
END //
DELIMITER ;
```

**Exercici 2**

```mysql

```

**Exercici 3**

```mysql

```

**Exercici 4**

```mysql

```

**Exercici 5**

```mysql

```

**Exercici 6**

```mysql

```

**Exercici 7**

```mysql

```

**Exercici 8**

```mysql

```
**Exercici 9**

```mysql

```
**Exercici 10**

```mysql

```

***

## Enunciat de Procediments

**Exercici 1**

```mysql

```

**Exercici 2**

```mysql

```

**Exercici 3**

```mysql

```

**Exercici 4**

```mysql

```

**Exercici 5**

```mysql

```

**Exercici 6**

```mysql

```

**Exercici 7**

```mysql

```

**Exercici 8**

```mysql

```
**Exercici 9**

```mysql

```
**Exercici 10**

```mysql

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

***
