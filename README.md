# 🫀 Prédiction du Risque de Maladie Cardiaque

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![R](https://img.shields.io/badge/R-4.0+-blue.svg)](https://www.r-project.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![GitHub](https://img.shields.io/badge/GitHub-Repository-black.svg)](https://github.com)

## 📋 Description du Projet

Ce projet présente une analyse complète pour la prédiction du risque de maladie cardiaque en utilisant des techniques d'apprentissage automatique. L'étude combine une analyse exploratoire approfondie avec l'implémentation et la comparaison de plusieurs algorithmes de classification.

## 🎯 Objectifs

- **Analyse exploratoire** : Comprendre les facteurs de risque cardiovasculaire
- **Préparation des données** : Nettoyer et préprocesser le dataset
- **Modélisation prédictive** : Développer et optimiser des modèles de classification
- **Évaluation comparative** : Comparer les performances des différents algorithmes
- **Interprétabilité** : Analyser l'importance des variables avec SHAP

## 📊 Dataset

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

## 🛠️ Technologies Utilisées

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

## 📁 Structure du Projet

```
heart-disease-prediction/
├── data/
│   ├── heart.csv                 # Dataset original
│   └── heart_cleaned.csv         # Dataset nettoyé
├── notebooks/
│   ├── analyse_exploratoire.R    # Analyse exploratoire en R
│   └── modelisation.ipynb        # Modélisation en Python
├── src/
│   ├── data_preprocessing.py     # Préparation des données
│   ├── model_training.py         # Entraînement des modèles
│   └── model_evaluation.py       # Évaluation et comparaison
├── results/
│   ├── plots/                    # Graphiques et visualisations
│   └── models/                   # Modèles sauvegardés
├── README.md
└── requirements.txt
```

## 🔄 Méthodologie

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

## 📈 Résultats

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

## 📊 Captures d'Écran

<details>
<summary>🔍 Cliquez pour voir les visualisations</summary>

### 1. Distribution des Variables
<p align="center">
  <img src="results/plots/distribution_age.png" alt="Distribution Age" width="600">
  <br>
  <em>Distribution de l'âge des patients</em>
</p>

### 2. Matrice de Corrélation
<p align="center">
  <img src="results/plots/correlation_matrix.png" alt="Correlation Matrix" width="600">
  <br>
  <em>Matrice de corrélation des variables numériques</em>
</p>

### 3. Analyse PCA
<p align="center">
  <img src="results/plots/pca_biplot.png" alt="PCA Biplot" width="600">
  <br>
  <em>Biplot PCA avec coloration selon la présence de maladie cardiaque</em>
</p>

### 4. Performances des Modèles
<p align="center">
  <img src="results/plots/model_comparison.png" alt="Model Comparison" width="800">
  <br>
  <em>Comparaison avant/après optimisation des hyperparamètres</em>
</p>

### 5. Courbes ROC
<p align="center">
  <img src="results/plots/roc_curves.png" alt="ROC Curves" width="600">
  <br>
  <em>Courbes ROC de tous les modèles</em>
</p>

### 6. Importance des Variables (SHAP)
<p align="center">
  <img src="results/plots/shap_summary.png" alt="SHAP Summary" width="700">
  <br>
  <em>Analyse SHAP de l'importance des variables</em>
</p>

### 7. Matrice de Confusion - Random Forest
<p align="center">
  <img src="results/plots/confusion_matrix_rf.png" alt="Confusion Matrix" width="500">
  <br>
  <em>Matrice de confusion du meilleur modèle (Random Forest)</em>
</p>

</details>

## 🚀 Installation et Utilisation

### Prérequis

#### Python 3.8+
```bash
pip install -r requirements.txt
```

#### R 4.0+
```r
# Installer les packages R nécessaires
install.packages(c("tidyverse", "skimr", "corrplot", "factoextra", "MASS"))
```

### Cloner le Repository
```bash
git clone https://github.com/username/heart-disease-prediction.git
cd heart-disease-prediction
```

### Exécution

#### 1. Analyse exploratoire (R)
```bash
Rscript notebooks/analyse_exploratoire.R
```

#### 2. Modélisation (Python)
```bash
jupyter notebook notebooks/modelisation.ipynb
# ou
python src/model_training.py
```

## 📋 Requirements

Créez un fichier `requirements.txt` avec :

```txt
pandas==1.5.3
numpy==1.24.3
scikit-learn==1.3.0
xgboost==1.7.6
shap==0.42.1
matplotlib==3.7.1
seaborn==0.12.2
jupyter==1.0.0
plotly==5.14.1
```

## 🔍 Insights Clés

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

## 🤝 Contributions

Les contributions sont les bienvenues ! Merci de :
1. Forker le projet
2. Créer une branche feature (`git checkout -b feature/AmazingFeature`)
3. Committer les changements (`git commit -m 'Add AmazingFeature'`)
4. Pousser vers la branche (`git push origin feature/AmazingFeature`)
5. Ouvrir une Pull Request

## 📄 Licence

Ce projet est sous licence MIT. Voir le fichier `LICENSE` pour plus de détails.

## 📧 Contact

**Nom** - [votre.email@example.com](mailto:votre.email@example.com)

**Lien du projet** : [https://github.com/username/heart-disease-prediction](https://github.com/username/heart-disease-prediction)

## 🙏 Remerciements

- Dataset fourni par [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/heart+disease)
- Communauté scikit-learn pour les excellents outils de ML
- Équipe SHAP pour les outils d'interprétabilité

---

⭐ N'hésitez pas à mettre une étoile si ce projet vous a été utile !
