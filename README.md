# Emotion-Detection

![Emotions](https://cdn-images-1.medium.com/max/1600/1*6xp-IY-M8lEEEN0UuUBq0w.jpeg)

Petit projet sur la base de données (image, coord marqueurs du visage) pour classer des visage selon des émotions 

# Repository Files:
```
├── REAMDE.md
├── emotion.ipynb
├── img.png
├── res1.png
└── data
    ├── .json
    ├── .hdf5
    └── .csv
```

# Architecture

- On a 2 modèle, un pour prédire la localisation des marqueurs d'un visage, l'autre pour classifiier une émotion à partir d'une image)

# Dataset

1. data.csv
- Le .csv comprend les coords y, x des différent marqueurs du viasge (coin sup/inf gauche/droit oeil, pointe du nez, etc ...) + image (sous forme de chaine de caractère pour sauvegarder de l'espace)
- ![Résultats](https://github.com/Soren-Kierkegaard/Emotion-Detection/img.png)

2. icml_face_data.csv'
- Contient des images (aussi sous forme de chaine) associées à leur label respectif, labels = {0 : 'colere', 1 : 'degout', 2 : 'triste', 3 : 'joie', 4 : 'surprise'}

# Résultats

- A des fins démonstration et de rappel, j'ai concervé dans le notebook les différente traces d'entrainement des modèles / Voir

<table>
  <tr>
    <th> Précision Classification Emotion</th>
    <th> 80 % </th>
  </tr>
</table>

*On peut faire mieux avec un peu plus d'entrainement et équilibrant les données

![Résultats](https://github.com/Soren-Kierkegaard/Emotion-Detection/res1.png)

# Petit Plus [ Juin 2021 ]

- Ajout d'une serveurization par Tensorflow Serving

# Amélioration (Prototype)

- Une méthode par "Méta+Learning" (Neuro-évolution) pour apprendre la melleurs architecture possible d'un modèle poyr un problème.
- L'idée m'a été inspiré par le site https://www.datavaloris.com/fr/ai/notre-approche/ et la vidéo de Siraj Raval https://www.youtube.com/watch?v=2z0ofe2lpz4
- PEUT ETRE TRES TIME CONSUMING

# Acknowlege

- Originly coded in February. 2021, révisé en June 2021 
