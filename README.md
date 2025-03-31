# Débruitage des Signaux ECG par Modèle de Diffusion

## Description
Ce projet explore l'application des **modèles de diffusion** pour le **débruitage des signaux ECG**. L'objectif est d'entraîner un modèle à reconstruire un signal propre à partir d'un signal bruité, en intégrant les principales sources de bruit présentes dans les enregistrements ECG.
Ce travail s'inscrit dans la continuité du projet annuel sur les modèles de diffusion.

## Table des matières
1. [Introduction](#introduction)
2. [Données](#données)
3. [Ajout de bruit](#ajout-de-bruit)
4. [Modèle de diffusion](#modèle-de-diffusion)
5. [Résultats](#résultats)
6. [Pistes d'améliorations](#pistes-daméliorations)
7. [Prérequis](#prérequis)

## Introduction
Les signaux ECG sont souvent perturbés par divers bruits tels que le bruit de base, les artefacts musculaires et les interférences électriques. Ce projet vise à utiliser un **modèle de diffusion** pour améliorer la qualité des signaux et préserver leurs caractéristiques physiologiques essentielles.

## Données
Nous utilisons la base de données **PTB-XL ECG**, accessible sur [PhysioNet](https://physionet.org/content/ptb-xl/1.0.3/), qui comprend :
- **21 801 enregistrements ECG** de 10 secondes
- **12 canaux**
- **Annotations cliniques** détaillées

Les données sont réparties comme suit :
- **80%** pour l'entraînement
- **10%** pour la validation
- **10%** pour le test

## Ajout de bruit
Nous simulons divers types de bruit avec des **niveaux de SNR (Signal-to-Noise Ratio) entre 6 dB et 24 dB** :
- **Bruit gaussien blanc**
- **Bruit de baseline**
- **Mouvement d'électrode**
- **Artefacts musculaires**
- **Interférence électrique (50 Hz)**

Des visualisations sont générées pour comparer les signaux propres et bruités.

## Modèle de diffusion
### Architecture
- **U-Net modifié** pour traiter les séries temporelles
- **Transformations spectrales** pour mieux capturer les structures du signal

L'entraînement du modèle repose sur l'inversion progressive du bruit ajouté.

## Résultats
### Évaluation
Les performances sont mesurées à l'aide des métriques suivantes :
- **MSE (Mean Squared Error)**
- **SNR après débruitage**
- **Corrélation entre le signal reconstruit et le signal original**

### Visualisation
Nous analysons visuellement les comparaisons entre :
- Signal original vs signal bruité
- Signal original vs Signal bruité vs signal débruité

## Pistes d'améliorations
- Adapter la **fonction de perte** en tenant compte du SNR et du type de bruit
- Tester **d'autres architectures**
- Intégrer des **mécanismes d'interprétabilité**
- Explorer une **approche semi-supervisée** pour une meilleure généralisation

### Prérequis
- Wfdb
- PyTorch
- Scipy.signal
- ScikitLearn
- NumPy, Pandas, Matplotlib
