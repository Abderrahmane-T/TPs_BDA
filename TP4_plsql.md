# Exercice 1 

---

### 1. Ecrire une procédure anonyme PL/SQL qui permet de demander à un utilisateur de saisir deux entiers et d’afficher leur somme.

```sql
-- SERVER OUTPUT ON 

DECLARE
-- a NUMBER:= &a;
-- b NUMBER := &b;

    a NUMBER:=5;
    b NUMBER:=3;
    somme NUMBER;
BEGIN
    DBMS_OUTPUT.ENABLE;

    somme := a + b;
    DBMS_OUTPUT.PUT_LINE('La somme vaut : ' || somme);
END;
/
```
Ici, on réalise la somme entre a et b qui sont fixées à 5 et 3 (notation &a, &b semblent ne pas fonctionner en PL/SQL) respectivement et affichons le résultat par DBMS_OUTPUT 

_Il n'a pas été possible de faire le code avec a=&a (si cela aurait été possible, l'exécution de ce code avec l'usage de ce qui y a été mis en commentaire aurait été ma première réponse)_

---

### 2. Écrire une procédure anonyme PL/SQL qui permet de demander `a un utilisateurde saisir un nombre et d’afficher sa table de multiplication.

```sql
-- SET SERVEROUTPUT ON
-- ACCEPT a NUMBER PROMPT 'Veuillez saisir une valeur pour laquelle vous voulez la table de multiplication :';

DECLARE
    a NUMBER;
BEGIN
    DBMS_OUTPUT.ENABLE;

    a :=5;
    FOR i IN 1..10 LOOP
        DBMS_OUTPUT.PUT_LINE(a || ' x ' || i || ' = ' || (a * i));
    END LOOP;
END;
/
/
```

Pour cette question, on réalise la multiplication de a par i, où i va de 1 à 10, et affichons à chaque itération de la boucle, la multiplication réalisée ainsi que son résultat. De cette manière, une fois que l'exécution de la boucle se termine, la table de multiplication de a aura été affichée. 

_Encore une fois, il n'a pas été possible de faire le code avec a=&a (si cela aurait été possible, l'exécution de ce code avec l'usage de ce qui y a été mis en commentaire aurait été ma première réponse)_

---

### 3. Écrire une fonction r´ecursive qui permet de retourner xn, x et n sont deux entiers positifs

```sql

CREATE OR REPLACE FUNCTION puissance(x NUMBER, n NUMBER)
RETURN NUMBER IS
BEGIN
    IF n = 0 THEN
        RETURN 1; 
    ELSE
        RETURN x *puissance(x,n-1 ); 
    END IF;
END;
/

```

Je commence donc par créer cette fonction dans la section 'SQL SCripts' avant de pouvoir appeler la fonction, dans la section 'SQL Commadnds', de la manière suivante : 

```sql

BEGIN
    DBMS_OUTPUT.ENABLE;
    DBMS_OUTPUT.PUT_LINE(puissance(2, 3));
END;
/
```

Ce qui nous donnera le résultat de 2³.
