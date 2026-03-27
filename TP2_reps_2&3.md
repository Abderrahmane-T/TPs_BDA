# TAÏBI Abderrahmane - n°12411518

---

# Exercice 2 :
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

## 2. R(A, B, C) avec F = { A → C ; A → B }

### Clé candidate

- A → B et A → C ⟹ A → B, C  

Clé candidate : **A**

### Vérification des formes normales

Toutes les dépendances fonctionnelles ont une clé comme déterminant.

La relation est donc en :
- 3NF
- BCNF

### Finalement :

La relation est déjà en **BCNF**.  
Aucune décomposition n’est nécessaire.



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

### Finalement :

La relation est décomposée en deux relations en **BCNF** :
- R1(C, B)
- R2(A, C)





# Exercice 3 — Dépendances fonctionnelles et normalisation

---

## Soit une relation R(A, B, C, D, E) et un ensemble de d´ependances fonctionnelles
F = {A −→ B, C; C, D −→ E; B −→ D; E −→ A}. D´eduire au moins 16 d´ependances fonction-
nelles, en utilisant le syst`eme d’Amstrong (r`egles de r´eflexivit´e, augmentation et transitivit´e).

On considère :
F = { A → B, C ; C, D → E ; B → D ; E → A }

On utilise les axiomes d’Armstrong (réflexivité, augmentation, transitivité).

### Dépendances données

- A → B
- A → C
- CD → E
- B → D
- E → A

### Dépendances déduites

1. A → D (car A → B et B → D)
2. A → E (car A → C et A → D, donc CD → E)
3. A → A (réflexivité)
4. B → B (réflexivité)
5. C → C (réflexivité)
6. D → D (réflexivité)
7. E → E (réflexivité)
8. E → B (car E → A et A → B)
9. E → C (car E → A et A → C)
10. E → D (car E → B et B → D)
11. B → E (car B → D et avec C, CD → E — augmentation implicite)
12. A → B, C, D (union)
13. A → B, C, D, E (car A → E)
14. E → A, B, C (transitivité + union)
15. E → A, B, C, D (car E → D)
16. CD → A (car CD → E et E → A)

On obtient ainsi au moins 16 dépendances fonctionnelles.



## 2. Soit une relation R(A, B, C, D, E, F ) et un ensemble de d´ependances fonctionnelles
F = {A −→ B, C, D; B, C −→ D, E; B −→ D; D −→ A}

On considère :
F = { A → B, C, D ; BC → D, E ; B → D ; D → A }



### (a) Calculer la fermeture de l’attribut B et de l’ensemble {A, B}

#### Fermeture de B

B⁺ :

- B → D
- D → A
- A → B, C, D

Donc :
B⁺ = { B, D, A, C }



#### Fermeture de {A, B}

(A, B)⁺ :

- A → B, C, D
- BC → D, E
- B → D
- D → A

Donc :
(A, B)⁺ = { A, B, C, D, E }



### (b) Montrer que que {A, F } est une super-cl´e

(A, F)⁺ :

- A → B, C, D
- BC → E

Donc :
(A, F)⁺ = { A, B, C, D, E, F }

Conclusion : {A, F} est une **super-clé**.



### (c) Est-elle en BCNF (Boyce–Codd Normal Form) ? Si R n’est pas en BCNF, la d´ecomposer
pour atteindre cette forme normale.

#### Clés candidates

- A⁺ = { A, B, C, D, E }
- donc A n’est pas une clé (F manque)
- (A, F) est une clé

#### Vérification

- A → B, C, D : A n’est pas une clé 
- BC → D, E : BC n’est pas une clé 
- B → D : B n’est pas une clé 
- D → A : D n’est pas une clé 

Donc la relation **n’est pas en BCNF**.



### Décomposition

On peut décomposer selon B → D :

- R1(B, D)
- R2(A, B, C, E, F)

Puis continuer si nécessaire :

- Dans R2 : A → B, C ⟹ décomposition :
  - R3(A, B, C)
  - R4(A, E, F)



### Conclusion

Après décomposition, on obtient des relations en **BCNF**.



## 3. Soit une relation R(A, B, C, D, E) que l’on d´ecompose en deux relations



### (a) R1(A, B, C) et R2(A, D, E). Montrer que cette d´ecomposition est sans perte d’information.

Intersection : A

- A est une clé de R1 (car A → B, C)

Donc :
- jointure sans perte d’information

Conclusion : **décomposition sans perte**



### (b) R1(A, B, C) R2(C, D, E). Montrer que cette d´ecomposition est avec perte d’information

Intersection : C

- C n’est pas une clé de R1 ni de R2

Donc :
- jointure avec perte d’information

Conclusion : **décomposition avec perte**



