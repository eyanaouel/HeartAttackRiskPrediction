Prédiction du Risque de Maladie Cardiaque
📋 Description du Projet
Ce projet présente une analyse complète pour la prédiction du risque de maladie cardiaque en utilisant des techniques d'apprentissage automatique. L'étude combine une analyse exploratoire approfondie avec l'implémentation et la comparaison de plusieurs algorithmes de classification.
🎯 Objectifs

Analyse exploratoire : Comprendre les facteurs de risque cardiovasculaire
Préparation des données : Nettoyer et préprocesser le dataset
Modélisation prédictive : Développer et optimiser des modèles de classification
Évaluation comparative : Comparer les performances des différents algorithmes
Interprétabilité : Analyser l'importance des variables avec SHAP

📊 Dataset
Le dataset heart.csv contient 918 observations avec les variables suivantes :
Variables Numériques

Age : Âge du patient (années)
RestingBP : Tension artérielle au repos (mm Hg)
Cholesterol : Cholestérol sérique (mg/dl)
MaxHR : Fréquence cardiaque maximale atteinte
Oldpeak : Dépression du segment ST induite par l'exercice

Variables Catégorielles

Sex : Sexe (M/F)
ChestPainType : Type de douleur thoracique (ATA, NAP, ASY)
RestingECG : Résultats ECG au repos (Normal, ST, LVH)
ExerciseAngina : Angine induite par l'exercice (Y/N)
ST_Slope : Pente du segment ST (Up, Flat, Down)

Variable Cible

HeartDisease : Présence de maladie cardiaque (0 = Non, 1 = Oui)

🛠️ Technologies Utilisées
R

tidyverse : Manipulation et visualisation des données
corrplot : Matrices de corrélation
factoextra : Analyse PCA
MASS : Analyse discriminante linéaire (LDA)

Python

pandas, numpy : Manipulation des données
scikit-learn : Modèles de machine learning
xgboost : Gradient boosting
shap : Interprétabilité des modèles
matplotlib, seaborn : Visualisations
