# Infos Migrants — Marseille

Ce repo contient les infos de divers lieux d'aide et de services pour les personnes migrantes à Marseille et outils pour les visualiser.
Parmis ces outils il y a:
- Un site web :
  - Carte interactive de marseille
  - Liste avec les lieux et infos
  - Formulaire d'ajout de lieu
- Un flyer
  - Infos de lieux importants
  - Carte à mettre à jour

🗺️ **[Voir la carte](https://wandy-cinderroot.github.io/infos-migrants-marseille/)**

---

## Le site web
Par défaut le site montre la carte.
L'interface est disponible en français, anglais et arabe.
> [!NOTE]
> à mettre à jour avec les langues nécéssaires.

Les lieux sont séparé en 5 catégories associé chacune à un code couleur:
- **Manger** — distributions de repas et colis alimentaires
- **Journée / Douche** — accueils de jour, douches, vestiaires
- **Santé** — soins gratuits, PASS, planning familial
- **Papiers / Aide juridique** — droit d'asile, droit de séjour, accompagnement administratif
- **Cours de français** — niveaux débutant à avancé

### Carte des lieux
La carte est interactive. En cliquant sur un lieu, une bulle apparait avec les infos.

### Liste des lieux
Liste les lieux séparés par catégories. Affiche comme info:
- le nom du lieu
- l'adresse
- les horaires
- les notes

---
## Contribuer — ajouter ou modifier un lieu

### Option 1 — Formulaire (le plus simple)

Sur la carte, cliquez sur **＋ Proposer un lieu** et remplissez le formulaire. La suggestion nous parvient directement et nous l'ajoutons après vérification.

### Option 2 — Modifier un CSV sur GitHub

1. Ouvrez le fichier CSV correspondant à la catégorie dans le dossier `donnees/`
2. Cliquez sur l'icône crayon ✏️ en haut à droite du fichier
3. Ajoutez ou modifiez une ligne en respectant le format existant :

```
nom,adresse,horaires,notes
Nom du lieu,12 rue Example 13001 Marseille,Lundi 9h-12h,Arriver tôt
```

4. En bas de la page, cliquez sur **"Propose changes"** puis **"Create pull request"**

Un compte GitHub est nécessaire. Si vous n'en avez pas, utilisez le formulaire sur la carte.

### Format des données

Chaque ligne d'un CSV doit contenir :

| Colonne | Obligatoire | Exemple |
|---|---|---|
| `nom` | oui | Association Soleil |
| `adresse` | oui | 12 rue de la Paix 13001 Marseille |
| `horaires` | oui | Lundi et jeudi 9h-12h |
| `notes` | non | Arriver tôt, sans rendez-vous |

### Convertir CSV → GeoJSON

Après modification d'un CSV, il faut regénérer le GeoJSON correspondant. Utilisez [csv2geojson](https://csv2geojson.glitch.me) ou la commande suivante si vous avez Node.js :

```bash
npx csv2geojson --lat latitude --lon longitude donnees/manger/manger.csv > donnees/manger/manger.geojson
```

---

## Signaler une information obsolète

Ouvrez une [Issue](https://github.com/[username]/infos-migrants-marseille/issues) avec :
- Le nom du lieu concerné
- Ce qui a changé (horaires, adresse, fermeture…)
- Si possible, une source (site web, appel téléphonique…)

---

## Lancer le projet en local

```bash
git clone https://github.com/[username]/infos-migrants-marseille.git
cd infos-migrants-marseille
npx serve .
```

Puis ouvrir `http://localhost:3000` dans le navigateur.

> Ne pas ouvrir `index.html` directement depuis le système de fichiers (`file://`) — les fichiers GeoJSON ne se chargeront pas correctement.

---
## Structure du projet

```
infos-migrants-marseille/
│
├── index.html              # carte interactive
├── README.md
│
├── carte/
│   └── style.json          # style cartographique (Maputnik / OpenFreeMap)
│
├── donnees/
│   ├── manger/
│   │   ├── manger.csv
│   │   └── manger.geojson
│   ├── journee/
│   │   ├── journee.csv
│   │   └── journee.geojson
│   ├── sante/
│   │   ├── sante.csv
│   │   └── sante.geojson
│   ├── papiers/
│   │   ├── papiers.csv
│   │   └── papiers.geojson
│   └── francais/
│       ├── francais.csv
│       └── francais.geojson
│
├── icons/                  # icônes custom (sprite)
└── flyers/                 # supports de communication
```

---

## Technologies utilisées

- [MapLibre GL JS](https://maplibre.org/) — rendu de la carte
- [OpenFreeMap](https://openfreemap.org/) — tuiles vectorielles open source
- [Formspree](https://formspree.io/) — formulaire de suggestion
- Données : bénévoles et associations partenaires

---

## Licence
Les données et le code sont placés sous licence [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.fr).

Libres de réutilisation, modification et partage à condition de citer la source et de ne pas en faire un usage commercial.

---

*Carte maintenue par des bénévoles. Pour toute question : ouvrez une Issue ou utilisez le formulaire sur la carte.*
