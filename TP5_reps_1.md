# TAÏBI Abderrahmane - n°12411518

---

# Exercice 1 :
---  

## 1. Cr´eer la table transaction dont le script est donn´e ci-dessous, en utilisant la session S1

<img width="330" height="182" alt="1" src="https://github.com/user-attachments/assets/c45af89b-bd61-48cb-8848-ed620fd83c77" />

## 2. En utilisant la session S2, ins´erer quelques lignes, modifier une ligne, en supprimer une autre et enfin annuler les mises `a jour venant d’ˆetre effectu´ees avec la commande ROLLBAK. Afficher le contenu de la table.

### Ajout de trois transactions, 'transac1', 'transac2' et 'transac3' : 

<img width="496" height="310" alt="2" src="https://github.com/user-attachments/assets/43bc39ff-edfa-446a-b577-e1898ca0c44f" />

### Modification d'une information concernant la transaction d'identifiant 'transac2' :

<img width="358" height="162" alt="3" src="https://github.com/user-attachments/assets/dc35559d-bc4d-4566-bf20-7f6f66b08819" />

### Suppression de la transaction qui a 'transac1' pour identifiant :

<img width="350" height="145" alt="4" src="https://github.com/user-attachments/assets/832537e2-b89b-4229-867c-15f16bfc18cb" />

### Consultation du contenu de la table avant et après le ROLLBACK:

<img width="547" height="355" alt="5" src="https://github.com/user-attachments/assets/46eb3dac-b84d-48a8-9c7c-df54b3f50b65" />

#### Avant le rollback, les données ajoutées et modifiées sont conservées mais après le rollback, aucune d'entre elle ne figure : tout a été annulé.

## 3. Ins´erer `a nouveau dans transaction quelques lignes et clore avec la commande quit;. Consulter le contenu de la table, en utilisant la session S1. Que s’est-il pass´e ?

### Ajout de deux transactions via S_2 ('transac31' et 'transac32') avant de quitter avec "quit;":

<img width="774" height="365" alt="6" src="https://github.com/user-attachments/assets/a9e67fd1-02a8-4c76-b731-ca7f9808fa6f" />

### Consultation de la table via S_1 : 

<img width="549" height="179" alt="7" src="https://github.com/user-attachments/assets/936e77ca-6988-4d41-8c16-842a009ca9d2" />

#### On constate que l'ajout de transactions via S_2 ont été "commit" même si nous avons quitté S_2 avec "quit;". _(attendu??)_

## 4. 
