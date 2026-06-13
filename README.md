# Kaggle Competition: EPF Montpellier 2027

Ce dépôt contient le travail réalisé par l'équipe **les foufou de Sochaux** dans le cadre d'un projet d'école et de la compétition Kaggle : [EPF Montpellier 2027](https://www.kaggle.com/competitions/epf-montpellier-2027/overview).

**Membres de l'équipe :**
- Morotti Maxime
- Ribon Charlotte
- Stiffel Léopold

## Choix de Feature Engineering

Pour préparer et nettoyer notre dataset, nous avons appliqué les transformations suivantes sur nos features :
- **Encodage One-Hot (Variables muettes) :** Les variables catégorielles telles que `country`, `operatingSystem`, `browser`, `device`, `environmentType` et `articleSafenessCategorization` ont été transformées en variables binaires (get_dummies) afin d'être exploitables mathématiquement par notre modèle.
- **Suppression de variables (Drop) :** Nous avons choisi de retirer les variables `hashedRefererDeepThree` (identifiant très complexe / haute cardinalité) et `browserVersion` (trop spécifique) afin de réduire le bruit, alléger le jeu de données et éviter le surapprentissage.

## Modèle de Machine Learning Choisi

Nous avons opté pour le modèle **LightGBM** (Light Gradient Boosting Machine). 
Ce choix a été motivé par ses excellentes performances sur des données tabulaires volumineuses, sa rapidité d'entraînement, et sa capacité à traiter très efficacement des jeux de données contenant beaucoup de features creuses (comme c'est le cas après notre encodage One-Hot). De plus, un fichier `lgbm_best_model.pkl` et `best_params.json` ont été utilisés pour conserver la meilleure configuration.

## Résultat Obtenu

Notre modèle final a permis d'atteindre un **F1 Score de 0.76817**.

## Perspectives d'amélioration

Transformer en variables catégorielles les champs `placementId`, `websiteId` et en utilisant du target encoding, pour représenter correctement ces features pour l' entrainement du modèle.