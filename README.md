# NEXTBUY

> **Des Données Brutes aux Décisions Intelligentes**
> Analyse et prédiction du Comportement Client E-commerce

---

## Aperçu du Projet

NEXTBUY est un projet de data science développé pour analyser les données transactionnelles e-commerce et construire des modèles prédictifs capables de comprendre le comportement d'achat des clients.

Le projet suit trois étapes principales :

1. **Nettoyage et Prétraitement des Données**
2. **Analyse Exploratoire des Données (EDA)**
3. **Modélisation Prédictive**

Le résultat final fournit des insights actionnables pour optimiser le placement des produits, comprendre la fidélité client et prédire les comportements d'achat.

---

## Objectifs

* Nettoyer et prétraiter les données transactionnelles e-commerce
* Réaliser une analyse exploratoire avec des visualisations
* Identifier des segments clients via des techniques de clustering
* Construire des modèles prédictifs pour la probabilité de réachat et l'estimation de la taille du panier
* Fournir des recommandations business basées sur les données

---

## Structure du Répertoire

```
📁 NEXTBUY
├── data/
│   ├── aisles.csv
│   ├── departments.csv
│   ├── merged_clean.csv
│   ├── order_products.csv
│   ├── orders.csv
│   └── products.csv
├── notebook.ipynb
├── requirements.txt
└── README.md
```

### Description des Fichiers

| Fichier                  | Description                                                    |
| ------------------------ | -------------------------------------------------------------- |
| `requirements.txt`       | Dépendances du projet                                          |
| `notebook.ipynb`         | Analyse complète : nettoyage, EDA, clustering et modélisation  |
| `data/orders.csv`        | Informations sur les commandes (utilisateur, jour, heure, etc.)|
| `data/order_products.csv`| Produits par commande avec indicateur de réachat               |
| `data/products.csv`      | Noms des produits et liens de catégories                       |
| `data/aisles.csv`        | Noms des rayons                                                |
| `data/departments.csv`   | Noms des départements                                          |
| `data/merged_clean.csv`  | Dataset nettoyé et fusionné                                    |
| `README.md`              | Documentation du projet                                        |

---

# Étape 1 – Nettoyage et Prétraitement des Données

Réalisé dans **`notebook.ipynb`**

### Tâches Accomplies

* Chargement et fusion des datasets (orders, products, aisles, departments)
* Gestion des valeurs manquantes (dropna, fillna)
* Conversion des types de données (Int64 pour les entiers nullables)
* Corrections des valeurs de colonnes
* Export du dataset nettoyé et fusionné

### Sortie

* `data/merged_clean.csv`

---

# Étape 2 – Analyse Exploratoire des Données

Également réalisée dans **`notebook.ipynb`**

### Analyses Incluses

* Statistiques sur le nombre total de commandes et produits
* Calcul de la taille moyenne du panier
* Identification des produits les plus vendus
* Classement de popularité des départements
* Distribution des commandes par jour de la semaine
* Analyse du taux de réachat selon la position dans le panier
* Relation entre taille du panier et taux de réachat
* Analyse du premier produit ajouté au panier
* Score d'optimisation du placement en magasin
* Analyse des heures de pic et produits dominants
* Patterns de co-achat (analyse d'association)

Chaque visualisation inclut une interprétation écrite expliquant les insights et patterns découverts.

---

# Étape 3 – Segmentation Client et Modélisation Prédictive

Implémenté dans **`notebook.ipynb`**

### Clustering Client

Utilisation du clustering K-Means pour identifier 4 profils clients basés sur :
* Nombre total de commandes
* Jours moyens entre les commandes
* Position moyenne dans le panier
* Taux de réachat
* Heure moyenne de commande

### Profils des Clusters

| Cluster | Description                           |
| ------- | ------------------------------------- |
| 0       | Acheteurs réguliers, assez fidèles    |
| 1       | Acheteurs du soir, moins fidèles      |
| 2       | Meilleurs clients, très fidèles       |
| 3       | Petits acheteurs occasionnels         |

### Modèles Prédictifs

**Modèle 1 : Prédiction de Réachat**
* Cible : `reordered` (classification binaire)
* Features : user_id, product_id, order_dow, order_hour_of_day, days_since_prior_order, add_to_cart_order, aisle_id, department_id

**Modèle 2 : Prédiction de la Taille du Panier**
* Cible : `cart_size` (régression)
* Modèles comparés : Régression Linéaire vs Random Forest Regressor

### Métriques d'Évaluation

* MAE (Mean Absolute Error)
* R² Score

---

# Insights Business

### Recommandations de Placement Produit

* **Fruits et légumes frais** : Placer à l'entrée du magasin ou dans les allées centrales
* **Produits laitiers (yaourt, lait)** : Placement à hauteur des yeux dans les rayons frais
* **Produits du quotidien (eau, pain)** : Accès facile sans bloquer le trafic

### Stratégies de Ciblage Client

* **Cluster 2** : Programmes de fidélité prioritaires (meilleurs clients)
* **Cluster 0** : Maintenir l'engagement avec des offres personnalisées
* **Cluster 1** : Recommandations ciblées pour augmenter le taux de réachat
* **Cluster 3** : Campagnes de réactivation et offres de bienvenue

---

# Installation et Configuration

## Cloner le répertoire

```bash
git clone git@github.com:EpitechBachelorPromo2028/B-DAT-201-MAR-2-1-nextbuy-6.git
cd NEXTBUY
```

## Installer les dépendances

```bash
pip install -r requirements.txt
```

## Exécuter le notebook

Ouvrir `notebook.ipynb` dans VS Code et exécuter toutes les cellules.

---

# Technologies Utilisées

* Python
* pandas
* numpy
* matplotlib
* scikit-learn (KMeans, LinearRegression, RandomForestRegressor)

---

# Auteurs
- Louis Savon
- Matteo Castronovo

