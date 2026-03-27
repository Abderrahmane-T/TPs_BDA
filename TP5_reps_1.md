# TAÏBI Abderrahmane - n°12411518

---

# Exercice 1 :
---  

## 1. Cr´eer la table transaction dont le script est donn´e ci-dessous, en utilisant la session S1

<img width="330" height="182" alt="1" src="https://github.com/user-attachments/assets/c45af89b-bd61-48cb-8848-ed620fd83c77" />

***

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

***

## 3. Ins´erer `a nouveau dans transaction quelques lignes et clore avec la commande quit;. Consulter le contenu de la table, en utilisant la session S1. Que s’est-il pass´e ?

### Ajout de deux transactions via S_2 ('transac31' et 'transac32') avant de quitter avec "quit;":

<img width="774" height="365" alt="6" src="https://github.com/user-attachments/assets/a9e67fd1-02a8-4c76-b731-ca7f9808fa6f" />

### Consultation de la table via S_1 : 

<img width="549" height="179" alt="7" src="https://github.com/user-attachments/assets/936e77ca-6988-4d41-8c16-842a009ca9d2" />

#### On constate que l'ajout de transactions via S_2 ont été "commit" même si nous avons quitté S_2 avec "quit;". _(attendu??)_

***

## 4. Dans la session S1, ins´erer quelque lignes et fermer brutalement sqlplus. Reconnecter `a nouveau sur votre compte. Les donn´ees saisies ont-elles ´et´e pr´eserv´ees ?

### Je commecne par ajouter des données via la session S_1 : 

<img width="537" height="241" alt="8" src="https://github.com/user-attachments/assets/1563aeea-04da-4c1b-88a3-226a94b08ba3" />

### Puis je ferme brutalement le terminal utilisé pour cela :

<img width="638" height="201" alt="9" src="https://github.com/user-attachments/assets/2a33891d-e45f-48d5-ab8d-bb353a2e1827" />

### En rouvrant un terminal et me reconnectant, j'observe le contenu de la table : 

<img width="684" height="422" alt="10" src="https://github.com/user-attachments/assets/e9e1a25f-78df-4d87-8855-cc79c789d1e7" />

#### On constate que les deux lignes exécutées précédemment n'ont pas été prises en compte à cause de la fermeture brutale.

***

## 5. Dnas une nouvelle session, ins´erer quelques lignes et modifier la structure de la table transaction, en y ajoutant par exemple l’attribut val2transaction de type NUMBER(10). Ex´ecuter la commande ROLLBACK. Que s’est-il pass´e ?

### Ajout de données via la session S_3 et modification de la structure de la table transaction

<img width="557" height="273" alt="11" src="https://github.com/user-attachments/assets/e84d6aef-9043-4a97-8ea7-7416514f486d" />

### Exécution de "ROLLBACK;" et vérifications :

<img width="740" height="458" alt="12" src="https://github.com/user-attachments/assets/7f28e674-4481-491a-8849-68d9d2431961" />

#### On constate qu'aucune des modifications réalisées précédemment n'a été annulé par le ROLLBACK.

***

## 6. Conclure : d´efinir de mani`ere pr´ecise qu’est-ce qu’une session, une transaction et comment valider une transaction ou l’annuler.
