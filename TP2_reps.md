# TAÏBI Abderrahmane - n°12411518

# Exercice 2 — Normalisation des schémas de relations

On cherche, pour chaque relation, la forme normale la plus avancée (3NF, BCNF) et, si nécessaire, une décomposition.

---

## 1. R(A, B, C) avec F = { A → B ; B → C }

### Clé candidate

- A → B et B → C ⟹ A → C  
- Donc A → B, C  

Clé candidate : **A**

### Vérification des formes normales

- A → B : conforme (A est une clé)
- B → C : non conforme (B n’est pas une clé)

La relation n’est donc pas en BCNF.

- B → C viole aussi la 3NF car :
  - B n’est pas une clé
  - C n’est pas un attribut premier

La relation n’est donc pas en 3NF.

### Décomposition

On décompose selon la dépendance B → C :

- R1(B, C)
- R2(A, B)

### Vérification après décomposition

- R1(B, C) : B est clé ⟹ BCNF
- R2(A, B) : A est clé ⟹ BCNF

### Conclusion

La relation est décomposée en deux relations en **BCNF** :
- R1(B, C)
- R2(A, B)

---

## 2. R(A, B, C) avec F = { A → C ; A → B }

### Clé candidate

- A → B et A → C ⟹ A → B, C  

Clé candidate : **A**

### Vérification des formes normales

Toutes les dépendances fonctionnelles ont une clé comme déterminant.

La relation est donc en :
- 3NF
- BCNF

### Conclusion

La relation est déjà en **BCNF**.  
Aucune décomposition n’est nécessaire.

---

## 3. R(A, B, C) avec F = { AB → C ; C → B }

### Clés candidates

- AB → C ⟹ AB → A, B, C  
- C → B ⟹ AC → B ⟹ AC → A, B, C  

Clés candidates : **AB** et **AC**

### Vérification des formes normales

- AB → C : conforme (AB est une clé)
- C → B : non conforme (C n’est pas une clé)

La relation n’est pas en BCNF.

Cependant :
- B est un attribut premier (appartient à une clé candidate)

Donc la relation est en **3NF**, mais pas en BCNF.

### Décomposition

On décompose selon la dépendance C → B :

- R1(C, B)
- R2(A, C)

### Vérification après décomposition

- R1(C, B) : C est clé ⟹ BCNF
- R2(A, C) : aucune dépendance non triviale ⟹ BCNF

### Conclusion

La relation est décomposée en deux relations en **BCNF** :
- R1(C, B)
- R2(A, C)

---

## Conclusion générale

| Relation | Forme normale finale | Décomposition |
|----------|---------------------|--------------|
| 1        | BCNF                | Oui          |
| 2        | BCNF                | Non          |
| 3        | BCNF                | Oui          |
