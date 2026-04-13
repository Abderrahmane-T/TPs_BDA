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
    -- SET SERVEROUTPUT ON

BEGIN
    DBMS_OUTPUT.ENABLE;
    DBMS_OUTPUT.PUT_LINE(puissance(2, 3));
END;
/
```

Ce qui nous donnera le résultat de 2³.

---

### 4. ´Ecrire une proc´edure anonyme PL/SQL qui calcule la factorielle d’un nombre strictement positif saisi par l’utilisateur. Le résultat sera stock´e dans une table resultatFactoriel.

```sql

CREATE TABLE resultatFactoriel (
    nombre NUMBER,
    factorielle NUMBER
);
```
Je commence par créer une table resultatFactoriel comme demandé dans l'énoncé.

```sql

-- SET SERVEROUTPUT ON

DECLARE
    -- ACCEPT n NUMBER PROMPT 'Veuillez saisir la valeur pour laquelle vous souhaitez avoir la factorielle :'

    n NUMBER := 5; 
    k NUMBER := 1;
BEGIN

    FOR i IN 1..n LOOP
        k:=k *i;
    END LOOP;

    INSERT INTO resultatFactoriel VALUES (n, k);
    COMMIT;
END;
/

```

Puis, je crée la procédure anonyme qui va permettre de calculer "5!" en parcourant une boucle avec un indice qui va de 1 à 5 et qui, à chaque itération, change la valeur de k (valant 1 initialement).

Enfin, j'ajoute le couple formé par 5 et le résultat de 5! à la table.

_Encore une fois, il n'a pas été possible de faire le code avec a=&a (si cela aurait été possible, l'exécution de ce code avec l'usage de ce qui y a été mis en commentaire aurait été ma première réponse)_

---

### 5. Modifier le programme précédent pour qu’il calcule et stocke dans une table re-sultatsFactoriels les factorielles des 20 premiers nombres entiers.

```sql

-- SET SERVEROUTPUT ON

DECLARE 

    k NUMBER := 1;
BEGIN
    
    FOR i IN 1..20 LOOP

        k:=k *i;
        INSERT INTO resultatFactoriel VALUES (i, k);
    END LOOP;

    
    COMMIT;
END;
/

```

Je reprends donc le code de la question précédente et y retire l'utilisation de la variable n pour la remplacer par une boucle de i qui va de 1 à 20, calculant, au fur et à mesure, les i!.

On peut ensuite afficher les résultats grâce à la requête SQL suivante (où la table resultatFactoriel a déjà été créée à la question précédente) : 

```sql
SELECT * FROM resultatFactoriel
```

