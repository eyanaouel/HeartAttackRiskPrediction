#  Prédiction du Risque de Maladie Cardiaque



##  Description du Projet

Ce projet présente une analyse complète pour la prédiction du risque de maladie cardiaque en utilisant des techniques d'apprentissage automatique. L'étude combine une analyse exploratoire approfondie avec l'implémentation et la comparaison de plusieurs algorithmes de classification.

##  Objectifs

- **Analyse exploratoire** : Comprendre les facteurs de risque cardiovasculaire
- **Préparation des données** : Nettoyer et préprocesser le dataset
- **Modélisation prédictive** : Développer et optimiser des modèles de classification
- **Évaluation comparative** : Comparer les performances des différents algorithmes
- **Interprétabilité** : Analyser l'importance des variables avec SHAP

##  Dataset

Le dataset `heart.csv` contient **918 observations** avec les variables suivantes :

### Variables Numériques
- **Age** : Âge du patient (années)
- **RestingBP** : Tension artérielle au repos (mm Hg)
- **Cholesterol** : Cholestérol sérique (mg/dl)
- **MaxHR** : Fréquence cardiaque maximale atteinte
- **Oldpeak** : Dépression du segment ST induite par l'exercice

### Variables Catégorielles
- **Sex** : Sexe (M/F)
- **ChestPainType** : Type de douleur thoracique (ATA, NAP, ASY)
- **RestingECG** : Résultats ECG au repos (Normal, ST, LVH)
- **ExerciseAngina** : Angine induite par l'exercice (Y/N)
- **ST_Slope** : Pente du segment ST (Up, Flat, Down)

### Variable Cible
- **HeartDisease** : Présence de maladie cardiaque (0 = Non, 1 = Oui)

##  Technologies Utilisées

### R
- **tidyverse** : Manipulation et visualisation des données
- **corrplot** : Matrices de corrélation
- **factoextra** : Analyse PCA
- **MASS** : Analyse discriminante linéaire (LDA)

### Python
- **pandas, numpy** : Manipulation des données
- **scikit-learn** : Modèles de machine learning
- **xgboost** : Gradient boosting
- **shap** : Interprétabilité des modèles
- **matplotlib, seaborn** : Visualisations



##  Méthodologie

### 1. **Analyse Exploratoire (R)**
- Visualisation des distributions
- Analyse des corrélations
- Tests statistiques (Chi², ANOVA, Shapiro-Wilk)
- Analyse en Composantes Principales (PCA)
- Analyse Discriminante Linéaire (LDA)

### 2. **Préparation des Données (Python)**
- **Nettoyage** : Traitement des valeurs aberrantes (BP=0, Cholesterol=0)
- **Encodage** : 
  - Binaire pour Sex et ExerciseAngina
  - Ordinal pour ChestPainType et ST_Slope
  - One-hot pour RestingECG
- **Normalisation** : StandardScaler pour les variables numériques
- **Division** : 80% train / 20% test avec stratification

### 3. **Modélisation et Optimisation**

#### Algorithmes Implémentés
1. **Régression Logistique**
2. **Arbre de Décision**
3. **Random Forest**
4. **XGBoost**
5. **K-Nearest Neighbors (KNN)**
6. **Support Vector Machine (SVM)**

#### Optimisation
- **Validation croisée** à 5 plis
- **GridSearchCV** pour l'optimisation des hyperparamètres
- **Métriques d'évaluation** : Accuracy, Recall, F1-Score, AUC

##  Résultats

### Performances des Modèles (Après Optimisation)

| Modèle | Accuracy | Recall | F1-Score | AUC |
|--------|----------|--------|----------|-----|
| **Random Forest** | **0.90** | **0.92** | **0.91** | **0.93** |
| **XGBoost** | 0.87 | 0.89 | 0.89 | **0.93** |
| **SVM** | 0.87 | 0.90 | 0.88 | **0.93** |
| **Régression Logistique** | 0.88 | 0.91 | 0.89 | 0.91 |
| **Arbre de Décision** | 0.81 | 0.82 | 0.83 | 0.87 |
| **KNN** | 0.80 | 0.80 | 0.82 | 0.84 |

### Variables les Plus Importantes (Random Forest)
1. **ST_Slope** - Pente du segment ST
2. **ChestPainType** - Type de douleur thoracique
3. **MaxHR** - Fréquence cardiaque maximale
4. **ExerciseAngina** - Angine induite par l'exercice
5. **Age** - Âge du patient

##  Captures d'Écran

<details>
<summary> Cliquez pour voir les visualisations</summary>


<p align="center">
  <img src="https://github.com/eyanaouel/HeartAttackRiskPrediction/blob/12826e3329367aa72aaca755ccf8118e3d6a765c/Screenshot%202025-09-28%20135325.png" alt="ROC Curves of All Models" width="600">
  <br>
  <em>ROC Curves of All Models</em>
</p>

<p align="center">
  <img src="results/plots/correlation_matrix.png" alt="Correlation Matrix" width="600">
  <br>
  <em>Matrice de corrélation des variables numériques</em>
</p>

<p align="center">
  <img src="results/plots/pca_biplot.png" alt="PCA Biplot" width="600">
  <br>
  <em>Biplot PCA avec coloration selon la présence de maladie cardiaque</em>
</p>

<p align="center">
  <img src="results/plots/model_comparison.png" alt="Model Comparison" width="800">
  <br>
  <em>Comparaison avant/après optimisation des hyperparamètres</em>
</p>

<p align="center">
  <img src="results/plots/roc_curves.png" alt="ROC Curves" width="600">
  <br>
  <em>Courbes ROC de tous les modèles</em>
</p>

<p align="center">
  <img src="results/plots/shap_summary.png" alt="SHAP Summary" width="700">
  <br>
  <em>Analyse SHAP de l'importance des variables</em>
</p>

<p align="center">
  <img src="results/plots/confusion_matrix_rf.png" alt="Confusion Matrix" width="500">
  <br>
  <em>Matrice de confusion du meilleur modèle (Random Forest)</em>
</p>

</details>


##  Insights Clés

### Facteurs de Risque Identifiés
- **Pente du segment ST** : Variable la plus prédictive
- **Type de douleur thoracique** : ASY (Asymptomatique) = risque élevé
- **Fréquence cardiaque maximale** : Plus faible chez les patients malades
- **Angine induite par l'exercice** : Forte corrélation avec la maladie
- **Âge** : Risque croissant avec l'âge

### Recommandations Cliniques
1. **Attention particulière** aux patients avec pente ST "Down"
2. **Surveillance renforcée** des douleurs asymptomatiques
3. **Tests d'effort** pour évaluer MaxHR et ExerciseAngina
4. **Approche multi-factorielle** nécessaire pour le diagnostic

##  Contributions

Les contributions sont les bienvenues ! Merci de :
1. Forker le projet
2. Créer une branche feature (`git checkout -b feature/AmazingFeature`)
3. Committer les changements (`git commit -m 'Add AmazingFeature'`)
4. Pousser vers la branche (`git push origin feature/AmazingFeature`)
5. Ouvrir une Pull Request


