# 🚕 Analyse des réservations Uber en Inde – Delhi NCR

## 📌 Présentation du projet

Ce projet consiste à réaliser une analyse exploratoire des réservations Uber dans la région de Delhi NCR, en Inde.

L'étude repose sur un dataset contenant environ **150 000 réservations** enregistrées en 2024.

L'objectif est de comprendre le fonctionnement de l'activité, d'identifier les facteurs associés aux annulations de courses et d'étudier les performances des différents types de véhicules.

Une attention particulière est portée à la fiabilité du service, aux habitudes de réservation et aux facteurs susceptibles d'influencer l'expérience client.

## 🎯 Problématique

Dans un contexte de forte activité, pourquoi une part importante des réservations Uber n'aboutit-elle pas à un trajet complété ?

L'objectif est d'identifier les facteurs associés aux annulations et aux trajets incomplets afin de mieux comprendre les difficultés opérationnelles rencontrées par la plateforme.

## 🛠️ Technologies utilisées

- **Python** : programmation et analyse.
- **Pandas** : manipulation et nettoyage des données.
- **NumPy** : calculs numériques.
- **Matplotlib** : visualisation des données.
- **Seaborn** : exploration graphique.
- **Jupyter Notebook** : environnement d'analyse.
- **Git / GitHub** : gestion du projet.

## 🔎 Étapes du projet

### 1. Exploration et nettoyage des données
- Importation du dataset.
- Analyse de la structure des données.
- Vérification des valeurs manquantes.
- Contrôle des doublons.
- Correction des types de données.
- Préparation des variables nécessaires à l'analyse.

### 2. Analyse des annulations
- Étude des différents statuts de réservation.
- Comparaison des annulations par les chauffeurs et les clients.
- Analyse des réservations sans chauffeur disponible.
- Étude du temps d'attente avant la prise en charge (VTAT).

### 3. Analyse des performances des véhicules
- Comparaison des catégories de véhicules.
- Analyse du volume de réservations par type de véhicule.
- Étude des différences de performance selon les catégories.

### 4. Analyse temporelle
- Étude des réservations selon les heures.
- Analyse des tendances journalières.
- Comparaison des volumes mensuels.
- Identification des périodes de forte demande.

### 5. Analyse statistique et interprétation
Plusieurs hypothèses ont été étudiées afin d'identifier les facteurs associés aux échecs de réservation :

- Influence du type de véhicule.
- Influence des zones géographiques.
- Influence de la saisonnalité.
- Influence du mode de paiement.
- Influence du temps d'attente sur les annulations et la satisfaction.
- Influence de la valeur et de la distance du trajet.

## 📊 Principaux résultats

L'analyse met en évidence plusieurs constats :

- Environ **62 % des réservations** aboutissent à un trajet complété.
- Environ **18 %** sont annulées par les chauffeurs.
- Environ **7 %** sont annulées par les clients.
- Environ **7 %** correspondent à des réservations sans chauffeur disponible.
- Environ **6 %** sont classées comme incomplètes.

Ainsi, près de **38 % des réservations n'aboutissent pas à un trajet complété**.

L'analyse statistique montre notamment que le temps d'attente avant prise en charge (VTAT) est plus élevé pour les annulations clients que pour les trajets complétés.

Les autres hypothèses testées ne mettent pas en évidence de différences significatives avec les variables disponibles.

## 📁 Structure du projet

```text
Projet-Uber/
│
├── Data/
│   └── Dataset CSV
│
├── Nettoyage_Analyse.ipynb
├── Analyse.md
└── README.md
```

## 🚀 Installation et utilisation

### 1. Cloner le dépôt

```bash
git clone https://github.com/aoopen/Projet-Uber.git
cd Projet-Uber
```

### 2. Installer les dépendances

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 3. Ajouter les données

Vérifier la présence du dataset dans le dossier `Data/`.

### 4. Lancer le notebook

```bash
jupyter notebook
```

Ouvrir ensuite :

`Nettoyage_Analyse.ipynb`

Le fichier `Analyse.md` présente la synthèse des résultats et les principales conclusions de l'étude.

## ⚠️ Limites de l'analyse

- Les données concernent uniquement Delhi NCR et ne permettent pas de généraliser les résultats à toute l'Inde.
- Certaines variables économiques ne sont disponibles qu'après le démarrage du trajet.
- Il est donc difficile d'expliquer précisément certaines annulations de chauffeurs.
- Les résultats statistiques doivent être interprétés en tenant compte des limites du dataset.

## 💡 Compétences développées

- Data Cleaning
- Analyse exploratoire (EDA)
- Analyse statistique
- Analyse des comportements de réservation
- Analyse des performances opérationnelles
- Data Visualization
- Python et Pandas
- Interprétation et communication des résultats

---

**Projet d'analyse de données réalisé dans le cadre d'une étude de la performance opérationnelle d'une plateforme de mobilité.**
