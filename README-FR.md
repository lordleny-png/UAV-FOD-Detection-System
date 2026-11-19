# Système de détection des débris sur les pistes aéroportuaires par drone (UAV-FOD)

**Intelligence artificielle | Vision par ordinateur | YOLO11 | Technologie UAV**

## 1. Présentation du projet

Ce projet porte sur le développement d'un système d'intelligence artificielle capable de détecter et de classifier les objets étrangers présents sur les pistes aéroportuaires grâce à la vision par ordinateur.

Les débris étrangers, également appelés *Foreign Object Debris (FOD)*, peuvent être constitués de vis, boulons, pierres, fragments métalliques, matières plastiques, outils et autres objets susceptibles de présenter des risques pour les aéronefs.

L'objectif à long terme est d'intégrer un modèle de détection intelligent dans un drone (UAV) afin de contribuer à l'inspection automatisée des pistes d'aéroport.

**État actuel du projet :** préparation du jeu de données, entraînement du modèle et évaluation sur les données de validation.

## 2. Objectifs

- Détecter les objets étrangers présents dans les images.
- Identifier et classifier 31 catégories de débris.
- Étudier l'utilisation des drones pour l'inspection des pistes.
- Évaluer les performances du modèle de détection.
- Préparer le modèle à un futur déploiement embarqué et à l'inférence en temps réel.

## 3. Présentation du jeu de données

Le projet utilise le jeu de données FODPascalVOCFormat V2.1.

| Caractéristique | Description |
|---|---|
| Images originales | 33 793 |
| Catégories d'objets | 31 |
| Objets annotés (résumé du dataset) | 34 472 |
| Format initial des annotations | Pascal VOC (XML) |
| Format de conversion | YOLO (TXT) |

### Répartition des données

| Sous-ensemble | Images |
|---|---:|
| Entraînement | 20 235 |
| Validation | 5 059 |
| Test | 8 429 |
| **Total des images réparties** | **33 723** |

La préparation des données a comporté :
- La détection et la suppression des doublons dans les listes de répartition.
- La séparation des ensembles d'entraînement, de validation et de test.
- La conversion des annotations XML vers le format YOLO.
- La normalisation et la vérification des coordonnées des boîtes englobantes.
- La création du fichier de configuration `data.yaml`.

Le jeu de données complet n'est pas inclus dans ce dépôt.

## 4. Architecture du modèle et entraînement

Le modèle développé repose sur **YOLO11n**, une architecture légère de détection d'objets adaptée à l'expérimentation de solutions efficaces en vision par ordinateur.

### Configuration de l'entraînement

| Paramètre | Valeur |
|---|---|
| Modèle | YOLO11n |
| Nombre de classes | 31 |
| Nombre d'époques | 50 |
| Taille des images | 640 × 640 |
| Taille du batch | 16 |
| Poids préentraînés | YOLO11n |
| GPU | NVIDIA Tesla T4 |
| Framework | Ultralytics / PyTorch |
| Environnement | Google Colab |

## 5. Résultats de validation

Après l'entraînement, le modèle a obtenu les performances suivantes sur l'ensemble de validation :

| Indicateur | Résultat |
|---|---:|
| Précision | 99,7 % |
| Rappel | 99,3 % |
| mAP@50 | 99,3 % |
| mAP@50-95 | 91,6 % |

**Important :** ces résultats correspondent à l'ensemble de validation et non à l'ensemble de test. Une évaluation indépendante sur les données de test reste nécessaire pour mesurer la capacité de généralisation du modèle.

## 6. Technologies utilisées

- Python
- PyTorch
- Ultralytics YOLO11
- OpenCV
- NumPy
- Matplotlib
- Google Colab

## 7. Installation et utilisation

Cloner le dépôt :

```bash
git clone https://github.com/VOTRE_NOM_UTILISATEUR/UAV-FOD-Detection-System.git
cd UAV-FOD-Detection-System
```

Installer les dépendances :

```bash
pip install -r requirements.txt
```

### Effectuer une détection

Une fois les dépendances installées et les poids du modèle disponibles :

```python
from ultralytics import YOLO

model = YOLO("models/best.pt")

results = model.predict(
    source="chemin/vers/votre/image.jpg",
    conf=0.25,
    imgsz=640,
    save=True
)
```

Remplacer le chemin de l'image par celui de votre propre image de test.

## 8. Organisation du dépôt

```text
UAV-FOD-Detection-System/
│
├── README.md
├── README_FR.md
├── requirements.txt
├── .gitignore
├── notebooks/
├── models/
├── results/
├── docs/
└── assets/
```

## 9. Perspectives de développement

Les prochaines étapes du projet porteront notamment sur :
- L'évaluation du modèle sur des images prises depuis différentes altitudes de drone.
- L'amélioration de la détection des petits objets.
- L'étude de la robustesse du modèle face aux variations de luminosité et aux conditions environnementales.
- L'optimisation du modèle pour des plateformes embarquées comme NVIDIA Jetson.
- L'intégration du système dans un drone.
- Le développement d'un tableau de bord de suivi des détections.

## 10. Limites et sécurité

Ce projet constitue actuellement un prototype expérimental de recherche et de développement.

Des résultats élevés sur les données de validation ne garantissent pas la fiabilité en conditions réelles. Le modèle n'a pas encore été validé dans les conditions opérationnelles d'un aéroport ni approuvé pour prendre des décisions relatives à la sécurité aéronautique.

Les inspections humaines et les procédures officielles de sécurité aéroportuaire restent indispensables.

## 11. Auteur

**NYMBUSSEDE LENY NAPALA**

Data Analytics | Machine Learning | Computer Vision

GitHub : https://github.com/lordleny-png

---

*Ce projet explore les possibilités offertes par l'intelligence artificielle et les drones pour contribuer à l'inspection des pistes aéroportuaires et à la sécurité aéronautique.*
