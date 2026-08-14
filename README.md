#  Analyse et Gestion de Base de Données RH (SQL)

![SQL](https://img.shields.io/badge/Language-SQL-blue?style=for-the-badge&logo=sqlite&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![VS Code](https://img.shields.io/badge/IDE-VS_Code-007ACC?style=for-the-badge&logo=visual-studio-code&logoColor=white)
![Data Analysis](https://img.shields.io/badge/Focus-Data_Analysis-orange?style=for-the-badge)

##  Aperçu du Projet

Ce projet propose une solution complète de **gestion et d'analyse de données de ressources humaines (RH)** à l'aide de SQL. Il simule une base de données d'entreprise internationale regroupant 30+ collaborateurs répartis dans plusieurs pays et départements.

L'objectif est d'extraire des **insights clés pour la prise de décision RH** : masse salariale, répartition géographique, suivi des performances, filtres stratégiques et mises à jour de données.

---

##  Compétences & Concepts SQL Couverts

* **DDL & DML :** Création de tables (`CREATE TABLE`), insertion (`INSERT INTO`) et mise à jour de données (`UPDATE`).
* **Sélection & Filtrage :** Requêtes multi-critères (`WHERE`, `AND`, `OR`, `IN`, `BETWEEN`, `LIKE`).
* **Agrégation & Statistiques :** Calculs globaux et sectoriels (`SUM`, `AVG`, `COUNT`, `MIN`, `MAX`).
* **Analyse Groupée :** Segmentation fine et filtrage d'agrégats (`GROUP BY`, `HAVING`).
* **Tri & Restriction :** Classement dynamique et sous-ensembles (`ORDER BY`, `LIMIT`).
* **Gestion Temporelle :** Manipulations de dates et calculs d'ancienneté (`YEAR()`, `DATE_SUB()`, `CURDATE()`).

---

##  Exemples de Requêtes & Analyses Réalisées

### 1. Statistiques des Salaires & Groupements (`GROUP BY` & `HAVING`)
> *Identification des départements dont la masse salariale dépasse 200 000 $*
```sql
SELECT Departement, SUM(Salaire) AS MasseSalariale
FROM Employes 
GROUP BY Departement 
HAVING SUM(Salaire) > 200000;
```

### 2. Analyse de Performance & Rémunération (`WHERE`)
> *Sélection des profils hautement rémunérés (> 100k) mais sous-évalués (Note != 5)*

```sql
SELECT Prenom, Nom, Poste, Salaire, EvaluationPerformance 
FROM Employes 
WHERE EvaluationPerformance != 5 AND Salaire > 100000;
```

### 3. Analyse Temporelle d'Ancienneté
> *Filtrage des employés recrutés au cours des 5 dernières années*
```sql
SELECT Prenom, Nom, DateEmbauche 
FROM Employes 
WHERE DateEmbauche >= DATE_SUB(CURDATE(), INTERVAL 5 YEAR);


```
-- ============================================================
# I- CREATION ET INSERTION
-- ============================================================
```sql
CREATE TABLE Employes (
    ID INT PRIMARY KEY,
    Prenom VARCHAR(50),
    Nom VARCHAR(50),
    Email VARCHAR(100),
    Telephone VARCHAR(20),
    Poste VARCHAR(50),
    Departement VARCHAR(50),
    Salaire DECIMAL(10, 2),
    DateEmbauche DATE,
    EvaluationPerformance INT,
    Pays VARCHAR(50)
);
```
```sql
INSERT INTO Employes VALUES 
(1, 'Fabrice', 'Mutombo', 'fabrice.mutombo@gmail.com', '+243-811-123-456', 'Consultant', 'Finance', 118364.22, '2018-09-24', 2, 'RDC'),
(2, 'Fatou', 'Diop', 'fatou.diop@yahoo.com', '+221-78-456-7890', 'Développeur', 'Marketing', 31816.73, '2022-12-08', 3, 'Sénégal'),
(3, 'Aïssatou', 'Traoré', 'aissatou.traore@hotmail.com', '+225-07-456-1234', 'Consultante', 'Informatique', 105015.32, '2016-12-22', 4, 'Côte d’Ivoire'),
(4, 'Blaise', 'Ngoma', 'blaise.ngoma@exemple.com', '+243-812-789-456', 'Stagiaire', 'Informatique', 73687.95, '2020-07-26', 5, 'RDC'),
(5, 'Yassine', 'El Fassi', 'yassine.elfassi@gmail.com', '+212-06-123-7890', 'Designer', 'Opérations', 75700.8, '2018-01-11', 2, 'Maroc'),
(6, 'Mariam', 'Coulibaly', 'mariam.coulibaly@gmail.com', '+223-76-123-4567', 'Développeuse', 'Marketing', 115347.76, '2024-12-22', 4, 'Mali'),
(7, 'Dieudonné', 'Tshisekedi', 'dieudo.tshisekedi@exemple.com', '+243-813-456-789', 'Développeur', 'Informatique', 112556.95, '2016-10-15', 5, 'RDC'),
(8, 'Jacqueline', 'Abdoulaye', 'jacqueline.abdoulaye@exemple.com', '+228-90-123-4567', 'Développeuse', 'Informatique', 113483.58, '2018-10-07', 5, 'Togo'),
(9, 'Amadou', 'Cissé', 'amadou.cisse@yahoo.com', '+223-70-789-1234', 'Manager', 'Ressources Humaines', 75038.94, '2017-10-23', 5, 'Mali'),
(10, 'Chantal', 'Koffi', 'chantal.koffi@gmail.com', '+225-08-789-1234', 'Consultante', 'Ventes', 71006.17, '2018-01-08', 3, 'Côte d’Ivoire'),
(11, 'Adama', 'Sangaré', 'adama.sangare@exemple.com', '+223-65-456-1234', 'Consultant', 'Finance', 60185.82, '2020-07-28', 1, 'Mali'),
(12, 'Bintou', 'Diallo', 'bintou.diallo@hotmail.com', '+224-622-123-456', 'Stagiaire', 'Ventes', 77656.06, '2016-10-15', 2, 'Guinée'),
(13, 'Jean-Luc', 'Mokonzi', 'jeanluc.mokonzi@exemple.com', '+243-815-123-456', 'Consultant', 'Marketing', 61662.32, '2024-09-01', 2, 'RDC'),
(14, 'Amina', 'Benali', 'amina.benali@gmail.com', '+213-05-123-7890', 'Manager', 'Ventes', 102146.3, '2021-02-14', 2, 'Algérie'),
(15, 'Thierno', 'Ba', 'thierno.ba@gmail.com', '+221-77-789-1234', 'Développeur', 'Ressources Humaines', 90778.52, '2022-05-11', 5, 'Sénégal'),
(16, 'Luc', 'Durand', 'luc.durand@gmail.com', '+33-6-12-34-56-78', 'Analyste', 'Finance', 85000.50, '2019-04-10', 4, 'France'),
(17, 'Sophie', 'Dubois', 'sophie.dubois@outlook.com', '+32-474-12-34-56', 'Consultante', 'Informatique', 92000.00, '2021-06-15', 3, 'Belgique'),
(18, 'Hery', 'Rakoto', 'hery.rakoto@yahoo.fr', '+261-32-12-34-56', 'Responsable Marketing', 'Marketing', 65000.75, '2020-02-20', 4, 'Madagascar'),
(19, 'Clarisse', 'Ndikumana', 'clarisse.ndikumana@exemple.com', '+257-79-12-34-56', 'Développeuse Web', 'Informatique', 48000.60, '2018-11-01', 5, 'Burundi'),
(20, 'Yao', 'Komlan', 'yao.komlan@exemple.com', '+228-98-76-54-32', 'Consultant', 'Gestion', 54000.90, '2017-09-12', 4, 'Togo'),
(21, 'Ali', 'Mahamadou', 'ali.mahamadou@exemple.com', '+227-96-12-34-56', 'Analyste de Données', 'Informatique', 47000.00, '2016-05-30', 5, 'Niger'),
(22, 'Fatima', 'Djimadoum', 'fatima.djimadoum@exemple.com', '+235-99-12-34-56', 'Ingénieure Réseaux', 'Informatique', 49000.40, '2019-12-10', 4, 'Tchad'),
(23, 'Emily', 'Johnson', 'emily.johnson@gmail.com', '+1-202-555-0173', 'Data Scientist', 'Informatique', 120000.00, '2020-07-22', 5, 'États-Unis'),
(24, 'Alex', 'Smith', 'alex.smith@exemple.ca', '+1-613-555-0198', 'Analyste BI', 'Marketing', 82000.30, '2021-10-05', 3, 'Canada'),
(25, 'Pierre', 'Martin', 'pierre.martin@gmail.com', '+33-7-98-76-54-32', 'Chef de Projet', 'Opérations', 87000.00, '2017-02-18', 4, 'France'),
(26, 'Chantal', 'Van der Berg', 'chantal.berg@exemple.be', '+32-476-54-32-10', 'Développeuse Front-End', 'Informatique', 75000.25, '2022-03-30', 3, 'Belgique'),
(27, 'Jean', 'Randriamampianina', 'jean.randria@exemple.mg', '+261-33-12-34-56', 'Admin Systèmes', 'Informatique', 59000.00, '2021-12-12', 4, 'Madagascar'),
(28, 'Aimé', 'Ndayizeye', 'aime.ndayizeye@exemple.bi', '+257-78-34-12-56', 'Designer Graphique', 'Marketing', 40000.50, '2018-07-08', 5, 'Burundi'),
(29, 'Kossi', 'Mensah', 'kossi.mensah@exemple.tg', '+228-90-54-32-10', 'Spécialiste Logistique', 'Opérations', 52000.75, '2019-06-15', 4, 'Togo'),
(30, 'Aminatou', 'Idrissa', 'aminatou.idrissa@exemple.ne', '+227-94-54-32-10', 'Responsable Qualité', 'Opérations', 62000.90, '2020-09-25', 3, 'Niger');
```

-- ============================================================
# II- PARTIE 1 : SELECTIONS ET FILTRES DE BASE
-- ============================================================

### 1. Sélection de tous les employés

```sql
SELECT * FROM Employes;
```

### 2. Sélectionner tous les employés dont le pays est la RDC

```sql
SELECT * FROM Employes WHERE Pays = 'RDC';
```
### 3. Afficher uniquement les colonnes Prenom, Nom et Pays
```sql
SELECT Prenom, Nom, Pays FROM Employes;
```
### 4. Employés ayant un salaire supérieur à 90 000
```sql
SELECT * FROM Employes WHERE Salaire > 90000;
```

### 5. Employés embauchés après le 1er janvier 2020
```sql
SELECT * FROM Employes WHERE DateEmbauche > '2020-01-01';
```
### 6. Employés dont le prénom commence par la lettre 'A'

```sql
SELECT * FROM Employes WHERE Prenom LIKE 'A%';
```
### 7. Employés travaillant dans le département Informatique ou Finance
```sql
SELECT * FROM Employes WHERE Departement = 'Informatique' OR Departement = 'Finance';
```

-- ============================================================
# III- PARTIE 2 : COMPARAISON, PLAGE ET RECHERCHE PARTIELLE
-- ============================================================

### 1. Salaire entre 50 000 et 100 000
```sql
SELECT * FROM Employes WHERE Salaire BETWEEN 50000 AND 100000;
```
### 2. Poste contenant le mot 'Manager'
```sql
SELECT * FROM Employes WHERE Poste LIKE '%Manager%';
```
### 3. Évaluation de performance différente de 5
```sql
SELECT * FROM Employes WHERE EvaluationPerformance != 5;
```

### 4. Embauchés en 2021
```sql
SELECT * FROM Employes WHERE YEAR(DateEmbauche) = 2021;
```

### 5. Employés venant de France, Belgique ou États-Unis
```sql
SELECT * FROM Employes WHERE Pays IN ('France', 'Belgique', 'États-Unis');
```

-- ============================================================
# IV- PARTIE 3 : TRI ET LIMITES
-- ============================================================

### 1. Les 5 salaires les plus élevés
```sql
SELECT * FROM Employes ORDER BY Salaire DESC LIMIT 5;
```
### 2. Ordre croissant des dates d'embauche
```sql
SELECT * FROM Employes ORDER BY DateEmbauche ASC;
```
### 3. Les 3 premiers employés triés par performance décroissante
```sql
SELECT * FROM Employes ORDER BY EvaluationPerformance DESC LIMIT 3;
```

-- ============================================================
# V- PARTIE 4 : FONCTIONS D'AGREGATION
-- ============================================================

### 1. Salaire total
```sql
SELECT SUM(Salaire) AS SalaireTotal FROM Employes;

### 2. Salaire moyen du département Informatique
```sql
SELECT AVG(Salaire) AS SalaireMoyen FROM Employes WHERE Departement = 'Informatique';
```
### 3. Nombre total d'employés
```sql
SELECT COUNT(*) AS NombreEmployes FROM Employes;
```
### 4. Salaire minimum et maximum
```sql
SELECT MIN(Salaire) AS SalaireMin, MAX(Salaire) AS SalaireMax FROM Employes;
```
### 5. Nombre d'employés par département
```sql
SELECT Departement, COUNT(*) AS NombreEmployes FROM Employes GROUP BY Departement;
```

-- ============================================================
# VI- PARTIE 5 : GROUP BY ET HAVING
-- ============================================================

### 1. Salaire moyen par pays
```sql
SELECT Pays, AVG(Salaire) AS SalaireMoyen FROM Employes GROUP BY Pays;
```
### 2. Départements ayant plus de 3 employés
```sql
SELECT Departement, COUNT(*) AS NombreEmployes 
FROM Employes 
GROUP BY Departement 
HAVING COUNT(*) > 3;
```
### 3. Pays où le salaire moyen est supérieur à 70 000
```sql
SELECT Pays, AVG(Salaire) AS SalaireMoyen 
FROM Employes 
GROUP BY Pays 
HAVING AVG(Salaire) > 70000;
```

-- ============================================================
# VII- PARTIE 6 : INSERT ET UPDATE
-- ============================================================

> * Insertion d'un nouvel employé*
```sql
INSERT INTO Employes 
(ID, Prenom, Nom, Email, Telephone, Poste, Departement, Salaire, DateEmbauche, EvaluationPerformance, Pays) 
VALUES 
(31, 'Michel', 'Tamba', 'michel.tamba@exemple.com', '+243-818-456-789', 'Analyste', 'Finance', 60000.00, '2025-01-20', 4, 'Congo');
```
> *  Mise à jour du salaire de l'ID 5 *
```sql
UPDATE Employes SET Salaire = 80000.00 WHERE ID = 5;
```
> * Modification du département des développeurs (hommes et femmes)*
```sql
UPDATE Employes SET Departement = 'Développement' WHERE Poste LIKE 'Développe%';
```

-- ============================================================
# VIII- PARTIE 7 : CAS PRATIQUES
-- ============================================================

### 1. Embauchés dans les 5 dernières années (relatif à la date système)
```sql
SELECT * FROM Employes WHERE DateEmbauche >= DATE_SUB(CURDATE(), INTERVAL 5 YEAR);
```
### 2. Non évalués à 5 ET gagnant plus de 100 000
```sql
SELECT * FROM Employes WHERE EvaluationPerformance != 5 AND Salaire > 100000;
```

 ### 3. Départements dont la masse salariale dépasse 200 000
 ```sql
SELECT Departement, SUM(Salaire) AS MasseSalariale
FROM Employes 
GROUP BY Departement 
HAVING SUM(Salaire) > 200000;
```

### 4. Adresse email contenant 'gmail'
```sql
SELECT * FROM Employes WHERE Email LIKE '%gmail%';
```
