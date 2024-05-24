# Activitat Subprogrames

## Exercici 1 -  Funcions 
Exercici 1 - - Fes una funció anomenada spData, tal que donada una data en format MySQL ( AAAA-MM-DD ) ens retorni una cadena de caràcters en format DD-MM-AAAA. <br>
Exemple : SELECT spData('1988-12-01') => 01-12-1988

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
SELECT rrhh.sp_Data('1988-12-01');
```

## Exercici 2 -  Funcions 
Exercici 2 - Fes una funció anomenada spPotencia, tal que donada una base i un exponent, ens calculi la seva potència. Intenta no utilitzar la funció POW. <br>
Exemple : SELECT spPotencia(2,3) => 8 

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
SELECT sp_Potencia(2, 3);
```

## Exercici 3 -  Funcions 
Exercici 3 - - Fes una funció anomenada spIncrement que donat un codi d’empleat i un % de increment, ens calculi el salari sumant aquest percentatge. <br>
Per exemple, suposem que l’ empleat amb id_empleat = 124 té un salari de 1000 <br>
Exemple: SELECT spIncrement(124,10) obtindriem -> 1100

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
Exercici 4 - Fes una funció anomenada spPringat, tal que li passem un codi de departament, i ens torni el codi d’empleat que guanya menys d’aquell departament. 

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
Exercici 5 - Utilitzant la funció spPringat fes una consulta per obtenir de cada departament, l’empleat pringat. Mostra el codi i nom del departament, i el codi d’empleat.

```mysql
SELECT d.departament_id,sp_Pringat(d.departament_id) AS codi_empleat_pringat
FROM empleats d;
```

## Exercici 6 -  Funcions 
Exercici 6 - Fes una funció anomenada spCategoria, tal que donat un codi d’empleat, ens digui en quina categoria professional està. El criteri que volem seguir per determinar la categoria professional és en funció dels anys que porta treballant a l’empresa: <br>
Entre 0 i 1 anys -> Auxiliar <br>
Entre 2 i 10 anys -> Oficial de Segona <br>
Entre 11 i 20 Anys -> Oficial de Primera <br>
Més de 20 anys -> Que es jubili! <br>


```mysql
DROP FUNCTION IF EXISTS spCategoria;
DELIMITER //
CREATE FUNCTION spCategoria(codiEmpleat INT) RETURNS VARCHAR(50)
BEGIN
    DECLARE anys INT;
    DECLARE text_categoria VARCHAR(50);

    SELECT TIMESTAMPDIFF(YEAR, data_contractacio, CURRENT_DATE()) INTO anys
    FROM empleats
    WHERE empleat_id = codiEmpleat;

    IF anys >= 0 AND anys < 1 THEN
        SET text_categoria = 'Auxiliar';
    ELSEIF anys >= 2 AND anys <= 10 THEN
        SET text_categoria = 'Oficial de Segona';
    ELSEIF anys >= 11 AND anys <= 20 THEN
        SET text_categoria = 'Oficial de Primera';
    ELSE
        SET text_categoria = 'Que es jubili!';
    END IF;

    RETURN text_categoria;
END//
DELIMITER ;
 SELECT  spCategoria(empleat_id)
    FROM empleats

```

## Exercici 7 -  Funcions 
Exercici 7 - Fes una consulta utilitzant la funció anterior perquè mostri de cada empleat, el codi d’empleat, el nom, els anys treballats i la categoria professional a la que pertany.

```mysql

```

## Exercici 8 -  Funcions 
Exercici 8 - Fes una funció anomenada spEdat, tal que donada una data per paràmetre ens retorni l'edat d'una persona. Les dates posteriors a la data d'avui han de retornar 0.

```mysql

```

## Exercici 9 -  Funcions 
Exercici 9 - Fes una funció que ens retorni el número de directors (caps) diferents tenim.

```mysql

```

## Exercici 10 -  Funcions 
Exercici 10 - Quina instrucció utilitzarem si volem veure el contingut de la funció spPringat?

```mysql

```

***

## Exercici 1 - Procediments

Exercici 1 - Fes un procediment que permeti obtenir la data i hora del sistema i l’usuari actual. 

```mysql

```

## Exercici 2 - Procediments
Exercici 2 - Fes un procediment que intercanvii el sou de dos empleats passats per paràmetre.

```mysql

```

## Exercici 3 - Procediments
Exercici 3 - Fes un procediment que donat dos Ids d'empleat assigni el codi de departament del primer en el segon.

```mysql

```

## Exercici 4 - Procediments
Exercici 4 - Fes un procediment que donat dos codis de departament assigni tots els empleats del segon en el primer. Un cop executat el procediment el departament que correspont en el segon paràmetre ha de quedar desert/sense cap empleat.

```mysql

```

## Exercici 5 - Procediments
Exercici 5 - Fes un procediment per mostrar un llistat dels empleats. Volem veure el id_empleat, nom_empleat, nom_departament i el nom de la localització del departament.

```mysql

```

## Exercici 6 - Procediments
Exercici 6 - Fes un procediment que donat un codi d’empleat, ens doni la informació de l’empleat ( agafa la informació que creguis rellevant).

```mysql

```

## Exercici 7 - Procediments
Exercici 7 - Volem fer un registre dels usuaris que entren al nostre sistema. Per fer-ho primer caldrà crear una taula amb dos camps, un per guardar l’usuari i l’altre per guardar la data i hora de l’accés. 

```mysql

```

## Exercici 8 - Procediments
Exercici 8 - A continuació feu un procediment sense arguments, de manera que cada vegada que el crideu, insereixi en aquesta taula l’usuari actual i la data i hora en que s’ha executat el procediment.

```mysql

```

## Exercici 9 - Procediments
Exercici 9 - Fes un procediment que ens permeti afegir un nou departament però amb la següent particularitat: En cas que la localització no existeixi a la taula localitzacions, ens posarà un NULL en el camp id_localtizacio de la taula departaments. Al procediment li hem de passar el codi de departament, el nom del departament i el codi de la localització.

```mysql

```
## Exercici 10 - Procediments
Exercici 10 - Fes un procediment que donat un codi d’empleat, ens posi en paràmetres de sortida el nom i el cognom. Indica com ho pots fer per comprovar si el procediment et funciona.

```mysql

```

## Exercici 11 - Procediments
Exercici 11 - Fes un procediment que ens permeti modificar el nom i cognom d’un empleat. 

```mysql

```

## Exercici 12 - Procediments
Exercici 12 - Crea una taula d’auditoria anomenada logs_usuaris. Aquesta taula la utilitzarem per monitoritzar algunes de les accions que fan els usuaris sobre les dades,per exemple si actualitzen dades, eliminen registres.
La taula ha de tenir els següents camps:

| Nom | Tipus | Descripció |
| --- | --- | --- |
| usuari | VARCHAR(100)  | Usuari que ha realitzat l’acció |
| data   | DATETIME      | Data-Hora en que s’ha realitzat l’acció |
| taula  | VARCHAR(50)   | Taula sobre la que es realitza l’acció |
| accio  | VARCHAR(20)   | “ELIMINAR”,”AFEGIR”,”MODIFICAR”,”INSERIR” |
| valor_pk | VARCHAR(200) | valor que identifica el registre que ha patit l’acció |

Fes un procediment amb nom spRegistrarLog que rebrà com a paràmetres el nom de la taula, l’acció i el valor_pk.
Aquest procediment només cal que insereixi un registre en la taula logs_usuaris amb les dades rebudes, tenint en compte l’usuari actual i la data-hora del sistema.

```mysql

```

## Exercici 13 - Procediments
Exercici 13 - Fes un procediment que ens permeti eliminar un departament determinat. El departament s’ha d’eliminar de la taula departaments. Utilitza a més dins d’aquest procediment, el procediment creat anteriorment (spRegistrarLog) per guardar també un registre del que ha realitzat l’usuari. Ens ha de quedar clar que l’usuari actual, en data X ha eliminat de la taula DEPARTAMENTS el codi departament Y. <br>
Per exemple, si fem una crida al procediment per eliminar un departament:<br>
CALL eliminarDept(300);

```mysql

```

## Exercici 14 - Procediments
Exercici 14 - Fes un procediment que ens posi en paràmetres de sortida, el número d’empleats que tenim, el número de departaments i el número de localitzacions.

```mysql

```
