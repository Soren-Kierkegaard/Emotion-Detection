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

- Modèle de Détéction (Classification) :
 - Le modèle de base pour la détection est le modèle ResNet réemployé par Transfert Learning sur le jeu de donné 
![ResNet50-Archit](https://i.stack.imgur.com/gI4zT.png)

  - On a conserver que 2 sorties (la valeur de sortie est "oui" ou "Non"

- Modèle de segmentation
  - Le but de la segmentation est de catégoriser chaque pixel d'une image, la classification se fait donc au pixel près ("Dense Prediction")
  - ![Segmentation](https://miro.medium.com/max/700/1*nXlx7s4wQhVgVId8qkkMMA.png)
  - Le modèle de segmentation est une modèle type Unet (https://arxiv.org/abs/1505.04597).
  - Il se présente sous a forme d'une Full CNN-AE, c-à-d d'un réseau Autoencoeur dont les couches sont des couches Convolutionnelle (+ Pooling) et comme il n'y a aucune Couche Dense, il est Full Cnvolutional (FCN) ce qui permet de s'adapter a tout type de taille d'image.
  - ![Unet](https://miro.medium.com/max/700/1*OkUrpDD6I0FpugA_bbYBJQ.png)  
  - * Notre version est plus particulièrement une version ResUnet ( il y a des passerels entres la partie Encodeur et Décodeur)
  - ![img](https://upload.wikimedia.org/wikipedia/commons/2/2b/Example_architecture_of_U-Net_for_producing_k_256-by-256_image_masks_for_a_256-by-256_RGB_image.png)

# Mask ?

- Le but de la << segmentation d'images >> est de Comprendre l'image au niveau du pixel, et d'associer CHAQUE pixel à une classe. La sortie produite par le modèle de segmentation d'image se nomme "mask"

- Le mask est une version de l'image d'entrer soulignant en pixel blanc le point d'interet (255 s'il existe) et en noir tout le reste (=0)

  -> On pourra flatten la matrice representant le mask et norm les valeurs (Normaliser ces valeurs 255/0 --> 1/0 est un +)

  ![img](https://www.researchgate.net/profile/Svetlana-Yanushkevich/publication/343096300/figure/fig2/AS:915575563890689@1595301633452/Segmentation-masks-are-converted-to-bounding-box-masks-by-fitting-the-smallest-possible.png)
  
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
