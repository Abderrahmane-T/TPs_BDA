# Exercice 1 

---

## 1. Ecrire une procédure anonyme PL/SQL qui permet de demander à un utilisateur de saisir deux entiers et d’afficher leur somme.

```sql
DECLARE
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
Ici, on réalise la somme entre a et b qui sont fixées à 5 et 3 (notation &a, &b semble ne pas fonctionner en PL/SQL) respectivement et affichons le résultat par DBMS_OUTPUT 

## 2.
