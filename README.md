# 📊 Spark Crime Data Insights Project

## 📝 Description du projet

Ce projet a pour objectif de manipuler, nettoyer et analyser le dataset **Crimes in Chicago (2001 - présent)** à l’aide de **PySpark** dans Google Colab.
Il s’inscrit dans le cadre de mon **autoformation Big Data et Spark**, et vise à explorer un jeu de données massif de plus de **8 millions de lignes**.

L’objectif principal est de mettre en pratique les fonctionnalités de PySpark, depuis les opérations de base (nettoyage, typage, filtrage) jusqu’à des analyses plus avancées (fenêtres, SQL, UDF, pivot tables).

---

## 📂 Dataset utilisé

* **Nom** : Crimes – 2001 to Present
* **Source officielle** : [data.cityofchicago.org](https://data.cityofchicago.org/Public-Safety/Crimes-2001-to-Present/ijzp-q8t2)
* **Taille** : ~8 millions de lignes, 22 colonnes
* **Format** : CSV → transformé en Parquet pour une meilleure performance

---

## ⚙️ Installation & Configuration

### 1. Connexion Google Colab ↔ Google Drive

Montage du Drive pour accéder aux données et sauvegarder les résultats.

### 2. Installation des dépendances

* **PySpark** : moteur de traitement distribué
* **Findspark** : intégration Spark ↔ Python

### 3. Création d’une SparkSession

Point d’entrée de toute application Spark avec un nom personnalisé pour ce projet.

---

## 🏗️ Étapes du projet

### 1️⃣ Ingestion des données

* Lecture du fichier CSV brut
* Vérification du schéma et aperçu des premières lignes

### 2️⃣ Nettoyage & Typage

* Conversion des colonnes string → types appropriés (`IntegerType`, `BooleanType`, `DoubleType`, `TimestampType`)
* Exemple :

  ```python
  df = df.withColumn("Date", to_timestamp(col("Date"), "MM/dd/yyyy hh:mm:ss a"))
  ```

### 3️⃣ Exploration des données

* Affichage du nombre total de lignes et colonnes
* Aperçu de certaines colonnes clés (`Date`, `Primary Type`, `Arrest`, `Location`)
* Ajout d’une colonne constante `Dataset_Version`
* Vérification du nombre de types de crimes distincts

### 4️⃣ Analyses simples

* Nombre de crimes par type (`groupBy + count`)
* Nombre de crimes par lieu (`groupBy + orderBy`)
* Pourcentage de crimes menant à une arrestation

### 5️⃣ Analyses avancées

* **Pivot tables** : Arrestations par année
* **Window functions** : dernier crime enregistré par district
* **Valeurs manquantes** : détection colonne par colonne

### 6️⃣ SQL avec Spark

* Création d’une **vue temporaire** du DataFrame
* Requêtes SQL pour analyser les crimes menant à des arrestations par type et par année

### 7️⃣ UDF (User Defined Function)

* Création d’une fonction Python pour classifier les crimes (`Vol`, `Agression`, `Autre`)
* Transformation en UDF et ajout d’une colonne `Crime_Category`

### 8️⃣ Sauvegarde des résultats

* Export du DataFrame nettoyé et enrichi en format **Parquet**
* Sauvegarde dans **Google Drive** pour réutilisation ultérieure

---

## 📊 Résultats principaux

* Exploration d’un dataset de **8 millions de lignes**
* Analyses descriptives sur les types et lieux de crimes
* Calculs statistiques (taux d’arrestation, évolution par année)
* Mise en place d’outils avancés : **fenêtres, pivots, SQL, UDF**
* Sauvegarde optimisée en Parquet

---

## 🚀 Perspectives

Ce projet constitue une **base solide** pour l’apprentissage de PySpark.
L’étape suivante sera :

* D’élargir les **analyses** avec des fonctions statistiques plus poussées
* De couvrir la totalité des **fonctions PySpark** (DataFrame API, RDD API, MLlib, GraphFrames, etc.)
* D’intégrer des **dashboards** pour la visualisation interactive (ex. Power BI, Databricks, ou Plotly).
