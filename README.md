# Stage Projet 2 — Analyse de la circulation et des accidents

## Contexte
Ce dépôt contient le travail de mon **stage projet** (Stage Projet 2). L’objectif est d’analyser la circulation routière à partir des feux de signalisation et des collisions routières, puis de relier chaque accident à un feu via une jointure géographique. Les résultats alimentent un storytelling et un tableau de bord interactif (Power BI).

## Objectifs
- Explorer et comprendre les données (feux + accidents)
- Identifier des zones et périodes critiques
- Produire des tables analytiques pour un dashboard

## Données
Placez les fichiers sources dans `data/raw/` :
- `feux-circulation.csv`
- `collisions_routieres.csv`

## Méthodologie (résumé)
1. EDA légère (qualité, variables clés, coordonnées)
2. Préparation (dates, variables temporelles, nettoyage)
3. Jointure géographique (nearest neighbor + rayon adaptatif)
4. Création de tables analytiques
5. Export pour Power BI

## Notebook
- `notebooks/01_analyse_feux_accidents.ipynb`

Le notebook génère les exports suivants dans `data/processed/` :
- `accidents_avec_feux.csv`
- `accidents_par_feu.csv`
- `accidents_par_feu_heure.csv`
- `accidents_par_jour.csv`

## Tableau de bord (Power BI)
Utilisez les fichiers `data/processed/*.csv` comme sources, puis construisez :
- Page 1 : vue générale (KPI, trend, heatmap)
- Page 2 : hotspots par intersection
- Page 3 : analyse temporelle (jour/heure)

### Mettre le Power BI sur GitHub
- Si le fichier `.pbix` est **petit (< 50 Mo)**, vous pouvez le versionner normalement dans ce dépôt.
- S’il est **plus gros**, utilisez **Git LFS** (recommandé) ou publiez un export `.pdf`/`.png` dans `reports/`.

## Prérequis
- Python 3.x
- `pandas`, `numpy`, `scikit-learn`

## Structure du dépôt
- `data/` : données brutes et traitées
- `figures/` : visuels produits
- `notebooks/` : analyses et préparation des données
- `reports/` : livrables (export Power BI, captures, etc.)

## Auteur
- Votre nom
