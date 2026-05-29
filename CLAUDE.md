# CLAUDE.md — Accessibilité des équipements sportifs en France

## Ce projet en une phrase

Datavisualisation interactive sur l'accessibilité des équipements sportifs en
France (handicap moteur et sensoriel), construite à partir de la base DataES du
Ministère des Sports. Destinée à une communication LinkedIn.

## Fichiers du projet

```
index.html          — viz standalone (Chart.js), seul fichier à déployer
CLAUDE.md           — ce fichier
.vscode/settings.json
```

Pas de fichier de données local : les données sont chargées en live via l'API
DataES au chargement de la page, avec un fallback embarqué si l'API est
indisponible.

## Source de données

**Base des Équipements Sportifs (DataES)** — Ministère des Sports  
Site : https://equipements.sports.gouv.fr  
API (ODS Explore v2.1) :
```
https://equipements.sports.gouv.fr/api/explore/v2.1/catalog/datasets/data-es-equipement/
```

Les deux champs clés sont des champs **texte multivalués** (séparateur `;`) :
- `acces_handi_mobilite` — accessibilité handicap moteur
- `acces_handi_sensoriel` — accessibilité handicap sensoriel

Valeurs possibles par champ : Aire de jeu, Cheminements, Sanitaires,
Vestiaires, Accueil, Douches, Tribunes, Signalétique.

Base totale : **334 458 équipements** recensés.

### Endpoint utilisé dans index.html

```
GET /records
  ?select=acces_handi_mobilite,count(*) as nb
  &group_by=acces_handi_mobilite
  &order_by=nb desc
  &where=acces_handi_mobilite is not null
  &limit=20
```

Même appel pour `acces_handi_sensoriel`. Les valeurs contenant `;` (combinaisons
multi-sélection) sont filtrées côté JS — on ne garde que les valeurs atomiques.

⚠️ Le endpoint `/facets` de l'API ignore le paramètre `facet_name` et renvoie
toujours le facet `commune`. Ne pas l'utiliser pour ces champs.

## Ce que montre la viz

Deux graphiques horizontaux côte à côte (desktop) / empilés (mobile) :
- **Handicap moteur** (bleu `#1a73e8`) — top composants accessibles par volume
- **Handicap sensoriel** (vert `#00897b`) — idem

Tri : composant le plus renseigné **en haut**. Tooltip au survol : nombre
d'équipements + % sur le total de 334 458.

## Message éditorial (important)

L'angle n'est **pas critique** envers DataES — DataES est un client.  
Le message : *cette base est remarquablement complète sur l'accessibilité,
bien au-delà de ce qu'on trouve sur Google Maps ou d'autres sources.*

Ne pas introduire de notion de "taux de complétion insuffisant" ou de lacunes.

## Stack technique

- Chart.js 4.4.3 (CDN jsDelivr)
- HTML + CSS + JS vanilla, **aucun framework**
- Responsive : breakpoint 680px (côte à côte → empilé)
- Déploiement : **GitHub Pages** (fichier `index.html` à la racine)

## Prochaines étapes

1. Créer le dépôt GitHub `Accessibilite-Equipements-Sportifs-France`
2. Pousser `index.html`
3. Activer GitHub Pages (branche `main`, dossier racine)
4. Rédiger et publier le post LinkedIn

## Post LinkedIn — principes

- Court, naturel, jamais "généré par IA"
- Structure : accroche d'actualité → observation → source discrète → liens
- Laisser la viz porter les chiffres, ne pas les répéter dans le texte
- Proposer 2-3 options d'accroche, itérer avec l'utilisateur
