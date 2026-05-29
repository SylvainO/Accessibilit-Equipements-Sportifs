# Accessibilité des équipements sportifs en France

Datavisualisation interactive de l'accessibilité des équipements sportifs français pour les personnes en situation de handicap moteur et sensoriel.

## Données

**Source :** [Base des Équipements Sportifs (DataES)](https://equipements.sports.gouv.fr/explore/assets/data-es-equipement/) — Ministère des Sports  
**Mise à jour :** quotidienne  
**Total recensé :** 334 458 équipements

Les données sont chargées en direct via l'API publique DataES (ODS Explore v2.1). Un jeu de données de secours est embarqué dans la page si l'API est indisponible.

Les deux champs exploités sont des champs texte multivalués (séparateur `;`) :
- `acces_handi_mobilite` — accessibilité handicap moteur
- `acces_handi_sensoriel` — accessibilité handicap sensoriel

Composants renseignés : Aire de jeu, Cheminements, Sanitaires, Vestiaires, Accueil, Douches, Tribunes, Signalétique.

## Stack technique

- [Chart.js 4.4.3](https://www.chartjs.org/) (CDN jsDelivr)
- HTML + CSS + JavaScript vanilla — aucun framework
- Déployé sur **GitHub Pages** (`index.html` à la racine)

## Visualisation

Deux graphiques à barres horizontales :
- **Handicap moteur** — composants accessibles par volume d'équipements
- **Handicap sensoriel** — idem

Responsive : côte à côte sur desktop, empilés sur mobile (breakpoint 680 px).  
Tooltip au survol : nombre d'équipements + pourcentage sur le total.

## Lien

[Voir la visualisation](https://sylvaino.github.io/Accessibilit-Equipements-Sportifs/)
