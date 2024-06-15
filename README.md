## Projet de Machine Learning pour la Prédiction de l'Espèce de l'Iris

Ce projet vise à créer un système de prédiction de l'espèce de la fleur d'Iris en utilisant un pipeline de Machine Learning. Le projet utilise Streamlit pour le frontend, FastAPI pour le backend, MLflow pour la gestion des modèles, et Docker Compose pour le déploiement.

### Objectif

Le but de ce projet est de construire un système qui prédit l'espèce d'une fleur d'Iris en se basant sur des caractéristiques telles que la longueur et la largeur des sépales et des pétales. Ce système est conçu pour automatiser le processus de prédiction et de classification, améliorant ainsi la prise de décision dans des applications pratiques.

### Composants du Projet

1. **Acquisition et Prétraitement des Données** :
   - Chargement et préparation des données du dataset Iris.
   - Divisation des données en ensembles d'entraînement et de test.

2. **Entraînement de Modèles ML avec suivi MLflow** :
   - Utilisation de MLflow pour suivre les expériences d'entraînement et les modèles générés.
   - Entraînement d'un modèle de prédiction (par exemple, un classifieur SVM ou Decision Tree) sur le dataset Iris.

3. **Déploiement du Modèle via FastAPI** :
   - Création d'une API RESTful pour servir le modèle prédictif.
   - Utilisation de FastAPI pour gérer les requêtes entrantes et effectuer les prédictions.

4. **Interface Utilisateur avec Streamlit** :
   - Développement d'une interface web pour interagir avec le modèle via le point de terminaison FastAPI.
   - Utilisation de Streamlit pour créer une application web simple permettant aux utilisateurs de soumettre des données et de voir les prédictions.

5. **Containerisation avec Docker et Docker Compose** :
   - Conteneurisation de l'application et de ses services (frontend, backend, MLflow) avec Docker.
   - Utilisation de Docker Compose pour orchestrer les conteneurs et simplifier le déploiement.

6. **Gestion et Déploiement des Modèles avec MLflow** :
   - Entraînement, publication des experiences et enregistrement des modèles.  

### Structure du Projet

```
TP3/
│
├── backend/
│   ├── Dockerfile
│   ├── main.py                  # API FastAPI pour la prédiction
│   └── metrics.py               # Script pour entraîner le modèle et logguer les expériences MLflow
│
├── frontend/
│   ├── Dockerfile
│   └── main.py                  # Interface Streamlit pour l'utilisateur
│
├── mlflow/
│   ├── Dockerfile
│   ├── metrics.py               # Utilisé pour entraîner, évaluer et enregistrer les experiences du modèle
│   └── mlruns/                  # Répertoire pour les runs MLflow
│
├── models/
│   ├── model_2024_06_15_T03_14_31.pkl
│   ├── model_2024_06_15_T03_23_08.pkl
│   └── model.pkl               # Modèle prédictif entraîné
│
├── docker-compose.yaml         # Fichier pour orchestrer les services avec Docker Compose
│
└── README.md                   # Documentation du projet
```

### Instructions d'Utilisation

1. **Télecharger le dossier de travail** :
   - telecharger le fichier tp3.rar sur ce Git qui contient la structure montrée en haut.

2. **Accéder au dossier du projet tp3** :
   - Ouvrire le terminal et placez vous dans le repertoire racine tp3 .
     ```
     cd tp3
     ```
3. **Construction des dockers** :
   - Construisez et démarrez les services Docker
     ```
     docker-compose up --build
     ```
4. **Vérification** :
   - Une fois les services démarrés, les composants suivants seront disponibles :
     
   - Streamlit (Frontend) : http://localhost:8001
   - FastAPI (Backend) : http://localhost:8002/docs
   - MLflow : http://localhost:8003
     Changer le localhost si vous travaillez sur une machine distante ou virtuelle avec son IP.

### Entraînement du Modèle et enregistrement des experiences sur MlFlow

1. Connectez-vous au conteneur MLflow :
   ```bash
   docker exec -it mlflow bash
   ```

2. Exécutez le script pour entraîner le modèle :
   ```bash
   python3 /mlflow/metrics.py
   ```
   - Ce script entraînera un modèle sur le dataset Iris, évaluera sa performance, et sauvegardera le modèle dans le répertoire `models` avec un nom incluant un timestamp pour indiquer le moment de l'entraînement :
   - Exemple de nom de fichier : `model_2024_06_15_T03_14_31.pkl`
       
3. Vérifiez que le modèle a été enregistré dans le répertoire `/models` avec un suffixe de date pour identifier les fichiers de modèle sauvegardés.
   - accedez au MLflow : http://localhost:8003 et vérifier que votre experience est enregistrée avec les metrics

Ce guide fournit une vue d'ensemble complète du projet, des étapes de mise en place aux opérations courantes, pour assurer une gestion efficace du pipeline de Machine Learning.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
