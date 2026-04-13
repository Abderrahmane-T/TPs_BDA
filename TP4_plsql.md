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

---

# Exercice 2 

--- 

### 1. Ecrire un bloc anonyme qui permet d’ins´erer un nouveau employ´e, dont les valeurs des attributs matr, nom, sal, adresse et dep sont respectivement 4, Youcef, 2500, avenue de la R´epublique, 92002.

```sql
--SET SERVEROUTPUT ON;
DECLARE
    v_employe emp%ROWTYPE;
BEGIN
    DBMS_OUTPUT.ENABLE;

    v_employe.matr := 4;
    v_employe.nom := 'Youcef';
    v_employe.sal := 2500;
    v_employe.adresse := 'avenue Anatole France';
    v_employe.dep := 92000;
    
    -- Insertion d'un tuple dans la base
    INSERT INTO emp VALUES v_employe;
END;
/
```

Il s'agit ici d'un bloc anonyme permettant d'insérer l'employé Youcef avec la méthode "%ROWTYPE".

---

### 2. ´Ecrire un bloc anonyme qui permet de supprimer tous les clients dont le dep est connu, et utiliser la fonction ROW COU N T pour afficher le nombre de n-uplets supprim´es.

```sql
--SET SERVEROUTPUT ON;
DECLARE
    v_nb_lignes NUMBER;
BEGIN
    DBMS_OUTPUT.ENABLE;

    DELETE FROM emp WHERE dep = 10;
    v_nb_lignes := SQL%ROWCOUNT;
    dbms_output.put_line('v_nb_lignes : ' || v_nb_lignes);
END;
/
```

Il s'agit d'un bloc anonyme qui supprime les employés (ici du département de code 10) et utilise le curseur implicite SQL%ROWCOUNT pour récupérer et afficher le nombre de lignes supprimées.

---

### 3. ´Ecrire un bloc anonyme qui permet d’afficher la sommes des salaires de tous les employ´es, en utilisant un curseur explicite et la boucle LOOP AND LOOP. Cette proc´edure doit vous afficher le mˆeme r´esultat que la requˆete suivante :

```sql
--SET SERVEROUTPUT ON;
DECLARE
    v_salaire EMP.sal%TYPE;
    v_total EMP.sal%TYPE := 0;
    CURSOR c_salaires IS
        SELECT sal
        FROM emp;
BEGIN
    DBMS_OUTPUT.ENABLE;

    OPEN c_salaires;
    
    LOOP
        FETCH c_salaires INTO v_salaire;
        EXIT WHEN c_salaires%NOTFOUND;
        IF v_salaire IS NOT NULL THEN
            v_total := v_total + v_salaire;
        END IF;
    END LOOP;
    
    CLOSE c_salaires;
    dbms_output.put_line('total : ' || v_total);
END;
/
```

Ce bloc utilise un curseur explicite et une boucle LOOP aifn de parcourir les enregistrements un à un et calculer la somme totale des salaires.

---

### 4. Modifier la proc´edure pr´ec´edente pour calculer le salaire moyen. Cette proc´edure doit vous afficher le mˆeme r´esultat que la requˆete suivante :

```sql

--SET SERVEROUTPUT ON;
DECLARE
    v_salaire EMP.sal%TYPE;
    v_total EMP.sal%TYPE := 0;
    v_compteur NUMBER := 0;
    CURSOR c_salaires IS
        SELECT sal
        FROM emp;
BEGIN
    DBMS_OUTPUT.ENABLE;
    
    OPEN c_salaires;
    
    LOOP
        FETCH c_salaires INTO v_salaire;
        EXIT WHEN c_salaires%NOTFOUND;
        IF v_salaire IS NOT NULL THEN
            v_total := v_total + v_salaire;
            v_compteur := v_compteur + 1;
        END IF;
    END LOOP;
    
    CLOSE c_salaires;
    
    IF v_compteur > 0 THEN
        dbms_output.put_line('moyenne : ' || (v_total / v_compteur));
    END IF;
END;
/

```

Cette procédure ajoute un compteur à la boucle afin de pouvoir diviser la somme totale des salaires par le nombre d'employés et ainsi afficher la moyenne.

---

### 5. Modifier les deux proc´edures pr´ec´edentes, en utilisant la boucle FOR IN

```sql
--SET SERVEROUTPUT ON;
DECLARE
    v_total EMP.sal%TYPE := 0;
    v_compteur NUMBER := 0;
    CURSOR c_salaires IS
        SELECT sal
        FROM emp;
BEGIN
    DBMS_OUTPUT.ENABLE;

    FOR r_sal IN c_salaires LOOP
        IF r_sal.sal IS NOT NULL THEN
            v_total := v_total + r_sal.sal;
            v_compteur := v_compteur + 1;
        END IF;
    END LOOP;
    
    dbms_output.put_line('total : ' || v_total);
    
    IF v_compteur > 0 THEN
        dbms_output.put_line('moyenne : ' || (v_total / v_compteur));
    END IF;
END;
/
```

Ce bloc simplifie les calculs de somme et de moyenne en remplaçant l'ancienne boucle par une boucle FOR IN, qui gère automatiquement l'ouverture, la lecture et la fermeture du curseur.

---

### 6. ´Ecrire une proc´edure anonyme qui permet d’afficher les noms des employ´es du d´epartement 92000 et 75000, en utilisant un curseur param´etr´

```sql
SET SERVEROUTPUT ON;
DECLARE
    CURSOR c(p_dep EMP.dep%TYPE) IS
        SELECT dep, nom
        FROM emp
        WHERE dep = p_dep;
BEGIN
    FOR v_employe IN c(92000) LOOP
        dbms_output.put_line('Dep 1 : ' || v_employe.nom);
    END LOOP;
    
    FOR v_employe IN c(75000) LOOP
        dbms_output.put_line('Dep 2 : ' || v_employe.nom);
    END LOOP;
END;
/
```

Ce code définit un curseur paramétré par le numéro de département, puis l'appelle deux fois successivement avec les valeurs cibles via des boucles FOR IN.

---
