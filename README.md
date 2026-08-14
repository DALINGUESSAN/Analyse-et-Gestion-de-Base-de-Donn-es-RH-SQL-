# 🗄️ Analyse et Gestion de Base de Données RH (SQL)

![SQL](https://img.shields.io/badge/Language-SQL-blue?style=for-the-badge&logo=sqlite&logoColor=white)
![MySQL](https://img.shields.io/badge/Database-MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Data Analysis](https://img.shields.io/badge/Focus-Data_Analysis-orange?style=for-the-badge)

## 🎯 Aperçu du Projet

Ce projet propose une solution complète de **gestion et d'analyse de données de ressources humaines (RH)** à l'aide de SQL. Il simule une base de données d'entreprise internationale regroupant 30+ collaborateurs répartis dans plusieurs pays et départements.

L'objectif est d'extraire des **insights clés pour la prise de décision RH** : masse salariale, répartition géographique, suivi des performances, filtres stratégiques et mises à jour de données.

---

## 🛠️ Compétences & Concepts SQL Couverts

* **DDL & DML :** Création de tables (`CREATE TABLE`), insertion (`INSERT INTO`) et mise à jour de données (`UPDATE`).
* **Sélection & Filtrage :** Requêtes multi-critères (`WHERE`, `AND`, `OR`, `IN`, `BETWEEN`, `LIKE`).
* **Agrégation & Statistiques :** Calculs globaux et sectoriels (`SUM`, `AVG`, `COUNT`, `MIN`, `MAX`).
* **Analyse Groupée :** Segmentation fine et filtrage d'agrégats (`GROUP BY`, `HAVING`).
* **Tri & Restriction :** Classement dynamique et sous-ensembles (`ORDER BY`, `LIMIT`).
* **Gestion Temporelle :** Manipulations de dates et calculs d'ancienneté (`YEAR()`, `DATE_SUB()`, `CURDATE()`).

---

## 🔍 Exemples de Requêtes & Analyses Réalisées

### 1. Statistiques des Salaires & Groupements (`GROUP BY` & `HAVING`)
> *Identification des départements dont la masse salariale dépasse 200 000 $*
```sql
SELECT Departement, SUM(Salaire) AS MasseSalariale
FROM Employes 
GROUP BY Departement 
HAVING SUM(Salaire) > 200000;

### 2. Analyse de Performance & Rémunération (WHERE)
> *Sélection des profils hautement rémunérés (> 100k) mais sous-évalués (Note != 5)
```sql
SELECT Prenom, Nom, Poste, Salaire, EvaluationPerformance 
FROM Employes 
WHERE EvaluationPerformance != 5 AND Salaire > 100000;
