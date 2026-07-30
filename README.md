# 🗺️ Analyse Spatiale du Réseau de Transports et Mobilités Douces à Pau (64000)

![QGIS](https://img.shields.io/badge/QGIS-3.x-green?logo=qgis)
![SIG](https://img.shields.io/badge/Secteur-Analyse%20Spatiale-blue)
![Niveau](https://img.shields.io/badge/Cursus-L3%20MIASHS-orange)

Projet cartographique et d'analyse spatiale développé sous **QGIS**. Il vise à évaluer la couverture du territoire palois par le réseau de transports en commun (IDELIS) et son articulation avec le réseau de mobilités douces (pistes cyclables).

---

## 🗺️ Carte Produite (Mise en Page SIG)

![Carte de couverture des transports et pistes cyclables à Pau](EXPORT/carte_pau.png)

---

## 🎯 Objectifs & But du Projet

* **Mesurer l'accessibilité spatiale :** Évaluer le degré de couverture du territoire par le réseau IDELIS.
* **Analyser l'intermodalité :** Étudier le croisement entre arrêts de bus et réseau cyclable pour évaluer les possibilités de report modal.
* **Identifier les zones isolées :** Détecter les ruptures de continuité cyclable ou les zones péricentrales peu desservies.
* **Aide à la décision :** Concevoir une carte thématique normée exploitable par des décideurs en aménagement urbain.

---

## 🛠️ Étapes de Réalisation Détaillées (Workflow SIG)

### 1. Acquisition, Intégration et Normalisation des Données
- **Infrastructures vectorielles :** Chargement des couches de données géographiques au format `.geojson` / Shapefiles (localisation des arrêts de bus IDELIS, tracé des voies cyclables).
- **Fond de carte (Basemap) :** Intégration du fond OpenStreetMap vectoriel/raster pour contextualiser le tissu urbain palois.
- **Gestion des systèmes de coordonnées (CRS) :** Reprojection systématique de l'ensemble des couches spatiales vers le **RGF93 / Lambert-93 (EPSG:2154)**. Cette étape est cruciale pour réaliser des calculs de distances exacts exprimés en mètres.

### 2. Traitements Spatiaux et Modélisation sous QGIS
- **Zones d'influence (Buffers / Tampons) :** Création de zones tampons de distance (isodistances) autour des arrêts de bus pour modéliser la zone de chalandise piétonne acceptable autour du réseau.
- **Dissolution spatiale (Dissolve) :** Application d'un traitement de dissolution sur les tampons générés afin de fusionner les géométries chevauchantes et obtenir l'emprise globale de la zone couverte à l'échelle de l'agglomération (Pau, Lons, Billère, Bizanos).
- **Analyse d'intersection et de superposition (Overlay) :** Croisement spatial des zones de desserte obtenues avec le réseau des pistes cyclables pour identifier visuellement les sections d'itinéraires cyclables situées hors ou dans la zone d'influence des transports.

### 3. Sémiologie Graphique & Conception de la Carte
- **Hiérarchisation visuelle :**
  - **Violet avec opacité/transparence :** Représentation des surfaces d'isodistances pour laisser transparaître le fond de carte urbain.
  - **Ponctuels orange :** Localisation explicite de chaque arrêt de bus IDELIS.
  - **Linéaires vert vif :** Mise en valeur des voies cyclables pour assurer une excellente lisibilité de l'intermodalité.
- **Composeur d'impression (Print Layout) :**
  - Ajout des éléments fondamentaux de la sémiologie cartographique : titre explicatif, orientation (flèche du Nord), échelle graphique dynamique et légende exhaustive.
  - Export du produit cartographique final aux formats haute définition (PNG / PDF).

---

## 📊 Résultats & Synthèse

- **Analyse du centre-ville :** L'hypercentre palois ainsi que l'axe Université - Hôpital disposent d'une excellente densité de desserte en bus et de liaisons cyclables structurées.
- **Ruptures péricentrales :** Détection de discontinuités dans le réseau cyclable à mesure que l'on s'éloigne du cœur d'agglomération vers les communes périphériques.

---

## 📂 Architecture du Dépôt

```text
├── 📁 DATA/                                      # Données géographiques brutes et vectorielles
├── 📁 EXPORT/                                    # Export de la carte finale (Format PNG / PDF)
│   └── 🖼️ carte_pau.png                          # Visuel principal de la carte
├── 📄 Analyse spatiale de la mobilité durable... # Rapport d'analyse et synthèse
└── 📄 README.md                                  # Documentation du dépôt
