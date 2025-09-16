
# Application des GANs pour l'Augmentation de Données Audio de Congestion Routière

Ce projet, réalisé dans le cadre du diplôme d'ingénieur à l'ENET'COM, explore l'utilisation des **Réseaux Antagonistes Génératifs (GANs)** pour augmenter un jeu de données audio destiné à la classification des niveaux de congestion du trafic urbain. L'objectif est de surmonter le problème des jeux de données limités et déséquilibrés afin d'améliorer la performance des modèles d'apprentissage automatique.

##  contexte du projet

La gestion efficace du trafic urbain est un défi majeur. Les systèmes intelligents basés sur l'IA peuvent prédire les niveaux de congestion, mais leur efficacité dépend de la qualité et de la quantité des données d'entraînement. Les données audio (bruits de la circulation) représentent une alternative peu coûteuse aux capteurs visuels, mais les ensembles de données disponibles sont souvent de petite taille et les classes (faible, moyenne, forte congestion) sont mal réparties.

Ce projet propose une solution innovante en utilisant les GANs pour générer des données synthétiques (spectrogrammes audio) et ainsi créer un jeu de données plus riche et équilibré.

##  metodologia

Le processus global du projet est structuré en plusieurs étapes clés :

1.  **Collecte de Données** : Extraction d'enregistrements audio de trafic routier à partir de diverses vidéos d'environnements urbains disponibles en ligne.
2.  **Prétraitement des Données** :
    *   **Segmentation** : Découpage des fichiers audio en segments courts (5-10 secondes).
    *   **Annotation Manuelle** : Classification de chaque segment en trois catégories : `faible`, `moyenne` ou `élevée` congestion.
3.  **Conversion en Spectrogrammes** : Transformation des signaux audio en représentations visuelles (spectrogrammes) à l'aide de la bibliothèque `Librosa`. Ces images servent d'entrée pour les modèles.
4.  **Augmentation avec les GANs** :
    *   Entraînement d'un modèle GAN sur les spectrogrammes existants.
    *   Le **générateur** apprend à créer de nouveaux spectrogrammes réalistes.
    *   Le **discriminateur** apprend à distinguer les vrais spectrogrammes des faux, forçant le générateur à s'améliorer.
5.  **Création du Jeu de Données Final** : Intégration des spectrogrammes synthétiques de haute qualité au jeu de données initial pour équilibrer les classes, en particulier celles qui sont sous-représentées (`moyenne` et `élevée`).
6.  **Validation** : L'ensemble de données augmenté est ensuite utilisé pour entraîner et évaluer un modèle de classification, démontrant une amélioration notable de la précision.

## technologies et outils

*   **Langage** : Python
*   **Bibliothèques Principales** :
    *   **TensorFlow & Keras** : Pour l'implémentation et l'entraînement du modèle GAN.
    *   **Librosa** : Pour le traitement des fichiers audio et la génération des spectrogrammes.
*   **Environnement de Développement** : Jupyter Notebooks
*   **Gestion de Projet** : Jira

## résultats obtenus

L'application des GANs a permis d'obtenir des résultats significatifs :

*   **Rééquilibrage des Classes** : Le nombre d'exemples pour les catégories de congestion moyenne et élevée a été augmenté, corrigeant le déséquilibre initial du jeu de données.
*   **Amélioration des Performances** : Les modèles de classification entraînés sur les données augmentées ont montré une **amélioration notable de la précision** et une meilleure capacité à généraliser.
*   **Réduction du Surapprentissage (Overfitting)** : L'augmentation de la diversité des données a permis aux modèles d'être plus robustes et moins dépendants des spécificités du jeu de données initial.
*   **Convergence du Modèle GAN** : L'analyse des courbes de perte (loss) du générateur et du discriminateur a montré une stabilisation progressive, indiquant que le modèle a appris avec succès à générer des données synthétiques de qualité.

![Évolution des pertes du générateur et du discriminateur](https.storage.googleapis.com/snippets-production/public/249110000000_2001_1300.png)

## Comment utiliser ce projet

Pour répliquer ce projet, suivez les étapes ci-dessous :

1.  **Clonez le dépôt :**
    ```bash
    git clone https://github.com/votre-utilisateur/votre-repo.git
    cd votre-repo
    ```

2.  **Créez un environnement virtuel et installez les dépendances :**
    ```bash
    python -m venv env
    source env/bin/activate  # Sur Windows: env\Scripts\activate
    pip install -r requirements.txt
    ```

3.  **Structure des Données :**
    Assurez-vous que vos données audio sont organisées dans des dossiers correspondant à leurs classes (ex: `/data/faible`, `/data/moyenne`, `/data/elevee`).

4.  **Exécutez les notebooks :**
    *   `01_data_preprocessing.ipynb` : Pour segmenter l'audio et générer les spectrogrammes.
    *   `02_gan_training.ipynb` : Pour entraîner le modèle GAN sur vos données.
    *   `03_classification_model.ipynb` : Pour entraîner un modèle de classification sur le jeu de données augmenté.

## Remerciements

Ce projet a été élaboré par **Youssef Krichen** sous la supervision de **Mme Mouna ZOUARI** au **Centre de Recherche en Numérique de Sfax (CRNS)**. Un grand merci aux membres de l'**École Nationale d'Électronique et des Télécommunications de Sfax (ENET'COM)** pour leur soutien académique.
