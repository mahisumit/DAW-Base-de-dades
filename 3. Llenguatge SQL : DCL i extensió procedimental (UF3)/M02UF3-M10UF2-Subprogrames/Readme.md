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
DELIMITER //
DROP FUNCTION IF EXISTS sp_Potencia //
CREATE FUNCTION sp_Potencia (b INT, e INT) RETURNS BIGINT DETERMINISTIC
BEGIN
    DECLARE v_potencia BIGINT;
    IF b IS NOT NULL AND e IS NOT NULL THEN
        SET v_potencia = 1;
        WHILE e > 0 DO
            SET v_potencia = v_potencia * b;
            SET e = e - 1;
        END WHILE;
    END IF;
  
    RETURN v_potencia;
END //
DELIMITER ;
```

## Exercici 3 -  Funcions 
Exercici 3 - 

```mysql
DELIMITER //
CREATE FUNCTION sp_Increment(id_empleat INT, increment_p INT)
RETURNS DECIMAL(10,2) DETERMINISTIC
BEGIN
    DECLARE salari_actual DECIMAL(10,2);
    
    SELECT salari INTO salari_actual
    FROM empleats
    WHERE id_empleat = id_empleat
    LIMIT 1;
    
    IF salari_actual IS NULL THEN
        SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'No s''ha trobat cap empleat amb aquest id_empleat.';
    END IF;
    
    SET salari_actual = salari_actual + (salari_actual * (increment_p / 100));
    
    UPDATE empleats
    SET salari = salari_actual
    WHERE id_empleat = id_empleat;
    
    RETURN salari_actual;
END//
DELIMITER ;
SELECT rrhh.sp_Increment(212, 20);

```

## Exercici 4 -  Funcions 
Exercici 4 - 

```mysql
DELIMITER //
CREATE FUNCTION sp_Pringat(codi_d INT)
RETURNS INT
NOT DETERMINISTIC READS SQL DATA
BEGIN
    DECLARE empleat_menys_pagat INT;
    
    SELECT empleat_id INTO empleat_menys_pagat
    FROM empleats
    WHERE codi_d = codi_d
    ORDER BY salari ASC
    LIMIT 1;
    
    RETURN empleat_menys_pagat;
END//
DELIMITER ;
SELECT rrhh.sp_Pringat(60);
```

## Exercici 5 -  Funcions 
Exercici 5 - 

```mysql
SELECT d.departament_id,sp_Pringat(d.departament_id) AS codi_empleat_pringat
FROM empleats d;
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
