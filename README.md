# 🛒 Prédiction d'Intention d'Achat E-commerce (Projet 14)

Bienvenue sur le dépôt de mon projet d'analyse web (Web Analytics) et de Data Mining. L'objectif de ce projet est de construire un modèle de Machine Learning capable de prédire si la session de navigation d'un utilisateur sur un site e-commerce aboutira à une transaction (achat) ou non.

## 🎯 Contexte et Problématique
Dans l'industrie du e-commerce, comprendre le comportement des utilisateurs est crucial pour optimiser le taux de conversion. 
**Problématique :** Peut-on prédire si une session de navigation aboutira à un achat en se basant sur les données comportementales et techniques de l'utilisateur ?

Il s'agit d'une tâche de **classification binaire supervisée**, compliquée par un fort déséquilibre des classes (seulement ~15,5% des sessions aboutissent à un achat).

## 📊 Données (Dataset)
Les données proviennent de l'**UCI Machine Learning Repository** :
* **Dataset :** [Online Shoppers Purchasing Intention Dataset](https://archive.ics.uci.edu/dataset/468/online+shoppers+purchasing+intention+dataset)
* **Dimensions :** 12 330 sessions (lignes) et 18 variables (colonnes).
* **Variable cible (Target) :** `Revenue` (True = Achat, False = Pas d'achat).

## 🛠️ Démarche et Méthodologie
Le projet suit rigoureusement un processus de Data Science de bout en bout, structuré en 10 étapes dans le notebook Jupyter :

1. **Importation & Chargement** : Récupération automatisée via l'API `ucimlrepo`.
2. **Analyse Exploratoire (EDA)** : Étude de l'impact des variables `PageValues`, `ExitRates` et du type de visiteur sur l'acte d'achat.
3. **Qualité des données** : Nettoyage justifié des doublons causés par les bugs de tracking.
4. **Feature Engineering** : Création de 3 variables stratégiques (`total_pages`, `total_duration`, `is_returning_visitor`).
5. **Pré-traitement (Pipeline)** : Utilisation de `ColumnTransformer` (StandardScaler pour les variables numériques, OneHotEncoder pour les catégorielles) et séparation stratifiée des données.
6. **Modélisation** : Entraînement et comparaison de 4 algorithmes (Régression Logistique, Random Forest, Gradient Boosting, KNN).
7. **Évaluation** : Utilisation de métriques adaptées au déséquilibre des classes (PR-AUC, ROC-AUC, Recall, Matrice de confusion).

## 🏆 Résultats et Recommandations Marketing

* **Meilleur Modèle :** Le modèle **Gradient Boosting** a démontré les meilleures performances, particulièrement sur la métrique PR-AUC.
* **Feature Importance :** La variable `PageValues` (valeur de la page visitée) est le facteur prédictif le plus puissant, suivi par le temps passé sur le site (`total_duration`).
* **Optimisation Métier (Seuil de décision) :** En ajustant le seuil de prédiction de *0.5 à 0.2*, le modèle augmente significativement son taux de détection des acheteurs potentiels (Recall de 82%), minimisant ainsi les opportunités manquées (faux négatifs).

**Actions proposées :** Déclenchement de pop-ups promotionnels ciblés (ex: -5%) pour les visiteurs détectés comme "hésitants" par l'algorithme afin de forcer la conversion avant leur sortie du site.

## 🚀 Installation et Exécution

Pour reproduire cette analyse en local sur votre machine :

1. Clonez ce dépôt :
   ```bash
   git clone [https://github.com/HOUSSAM051/nom-du-depot.git](https://github.com/HOUSSAM051/nom-du-depot.git)
