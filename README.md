# Stage Projet 2 — Analyse spatio-temporelle des accidents autour des feux de circulation

## Contexte
Ce projet académique a pour objectif d'analyser les accidents routiers a proximite des feux de circulation a Montreal, puis de transformer cette analyse en un tableau de bord interactif sous Power BI.

La demarche couvre toute la chaine de travail :
- preparation et transformation des donnees sous Python ;
- jointure geographique entre collisions et feux de circulation ;
- creation de tables analytiques ;
- modelisation et visualisation dans Power BI ;
- redaction d'un rapport academique de synthese.

## Objectifs
- Comprendre la distribution des accidents a proximite des feux de circulation
- Identifier les intersections, arrondissements et periodes les plus critiques
- Etudier la gravite des collisions et l'exposition des usagers vulnerables
- Construire un tableau de bord decisionnel lisible, interactif et exploitable

## Donnees sources
Les fichiers sources sont stockes dans `data/raw/` :
- `feux-circulation.csv`
- `collisions_routieres.csv`

## Methode de traitement
Le traitement principal est realise dans le notebook :
- `notebooks/01_analyse_feux_accidents.ipynb`

### Etapes principales
1. Chargement des jeux de donnees feux et collisions
2. Nettoyage des variables utiles a l'analyse
3. Construction des variables temporelles (`heure`, `annee`, `mois`, `jour`, `jour_semaine`)
4. Nettoyage des coordonnees geographiques
5. Rattachement de chaque accident au feu de circulation le plus proche
6. Filtrage spatial avec un rayon adaptatif base sur la distribution des distances
7. Enrichissement des accidents avec les informations de contexte du feu associe
8. Production de tables analytiques exportees pour Power BI

### Technique de jointure geographique
Le rapprochement entre accidents et feux de circulation est realise avec une recherche du plus proche voisin sur coordonnees geographiques, via une structure `BallTree` et une distance de type `haversine`.

Cette approche permet :
- d'associer chaque collision au feu le plus proche ;
- de calculer une distance en metres ;
- d'eliminer les rattachements trop eloignes au moyen d'un rayon de coupure.

## Tables produites
Les exports generes par le notebook sont stockes dans `data/processed/` :
- `accidents_avec_feux.csv` : table detaillee principale utilisee dans Power BI
- `accidents_par_feu.csv` : nombre d'accidents par intersection / feu
- `accidents_par_feu_heure.csv` : nombre d'accidents par intersection et par heure
- `accidents_par_jour.csv` : nombre d'accidents par jour

## Tableau de bord Power BI
Le fichier principal du tableau de bord est :
- `dashboard_feux_accidents.pbix`

Le dashboard est organise en trois pages complementaires :

### 1. `Decideur`
Vue de pilotage des accidents, de la gravite et de l'evolution annuelle.

Contenu principal :
- KPI globaux ;
- evolution par rapport a l'annee precedente ;
- top 10 des intersections par nombre d'accidents ;
- evolution mensuelle du volume d'accidents.

### 2. `Securite routiere`
Vue orientee gravite et profils de risque.

Contenu principal :
- accidents graves et mortels ;
- top intersections graves ;
- analyse des usagers vulnerables ;
- lecture par arrondissement via une zone dynamique.

### 3. `Hotspots / Carte`
Vue spatiale et temporelle des zones critiques.

Contenu principal :
- carte des hotspots par intersection ;
- matrice d'intensite selon le jour et l'heure ;
- filtres par annee et arrondissement.

## Livrables
Les livrables actuels du projet sont :
- `dashboard_feux_accidents.pbix`
- `rapport stageprojet2.pdf`
- `reports/powerbi_theme_midnight_orbit.json`

## Prerequis
- Python 3.x
- `pandas`
- `numpy`
- `scikit-learn`
- Power BI Desktop

## Structure du depot
- `data/raw/` : donnees sources
- `data/processed/` : tables analytiques preparees pour Power BI
- `notebooks/` : notebook de preparation et d'analyse
- `figures/` : visuels exportes si necessaire
- `reports/` : theme Power BI et autres livrables annexes

## Auteur
- Paul Yvan Seka

## Encadrement
Ce projet est encadre par le professeur **Bob Antoine Menelas**.
