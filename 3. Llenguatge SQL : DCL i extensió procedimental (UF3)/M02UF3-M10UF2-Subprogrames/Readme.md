# Activitat Subprogrames

## Exercici 1 -  Funcions 
Exercici 1 -

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

## Exercici 2 -  Funcions 
Exercici 2 -  

```mysql

```

## Exercici 3 -  Funcions 
Exercici 3 - 

```mysql

```

## Exercici 4 -  Funcions 
Exercici 4 - 

```mysql

```

## Exercici 5 -  Funcions 
Exercici 5 - 

```mysql

```

## Exercici 6 -  Funcions 
Exercici 6 - 

```mysql

```

## Exercici 7 -  Funcions 
Exercici 7 - 

```mysql

```

## Exercici 8 -  Funcions 
Exercici 8 - 

```mysql

```

## Exercici 9 -  Funcions 
Exercici 9 - 

```mysql

```

## Exercici 10 -  Funcions 
Exercici 10 - 

```mysql

```

***

## Exercici 1 - Procediments

Exercici 1 - 

```mysql

```

## Exercici 2 - Procediments
Exercici 2 -

```mysql

```

## Exercici 3 - Procediments
Exercici 3 -

```mysql

```

## Exercici 4 - Procediments
Exercici 4 -

```mysql

```

## Exercici 5 - Procediments
Exercici 5 -

```mysql

```

## Exercici 6 - Procediments
Exercici 6 -

```mysql

```

## Exercici 7 - Procediments
Exercici 7 -

```mysql

```

## Exercici 8 - Procediments
Exercici 8 -

```mysql

```

## Exercici 9 - Procediments
Exercici 9 -

```mysql

```
## Exercici 10 - Procediments
Exercici 10 -

```mysql

```

## Exercici 11 - Procediments
Exercici 11 -

```mysql

```

## Exercici 12 - Procediments
Exercici 12 -

```mysql

```

## Exercici 13 - Procediments
Exercici 13 -

```mysql

```

## Exercici 14 - Procediments
Exercici 14 -

```mysql

```

***
