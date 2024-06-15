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
   - Entraînement et enregistrement des modèles.  

### Structure du Projet

```
TP3/
│
├── backend/
│   ├── Dockerfile
│   ├── main.py                   # API FastAPI pour la prédiction
│   └── metrics.py               # Script pour entraîner le modèle et logguer les expériences MLflow
│
├── frontend/
│   ├── Dockerfile
│   └── main.py                  # Interface Streamlit pour l'utilisateur
│
├── mlflow/
│   ├── Dockerfile
│   ├── metrics.py               # Utilisé pour entraîner et évaluer le modèle
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

1. **Démarrer les Conteneurs** :
   - Exécutez `docker-compose up` dans le répertoire du projet pour démarrer tous les services.

2. **Accéder à l'Interface Utilisateur** :
   - Accédez à `http://localhost:8001` pour utiliser l'interface Streamlit et soumettre des données pour prédiction.

3. **Utiliser l'API** :
   - Utilisez un outil comme Postman ou cURL pour envoyer des requêtes POST à `http://localhost:8002/predict` avec les données d'entrée.

4. **Vérifier les Experiments MLflow** :
   - Ouvrez `http://localhost:8003` pour accéder à l'interface web de MLflow et visualiser les expériences et modèles.

### Entraînement du Modèle

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

### Commandes pour GitHub

Pour supprimer un fichier sur GitHub :
1. Allez sur la page principale de votre dépôt sur GitHub.
2. Naviguez jusqu'au fichier que vous souhaitez supprimer.
3. Cliquez sur le fichier, puis sur le bouton "Delete" (Supprimer) dans le coin supérieur droit.
4. Confirmez la suppression en cliquant sur "Commit changes" (Valider les modifications).

---

Ce guide fournit une vue d'ensemble complète de votre projet, des étapes de mise en place aux opérations courantes, pour assurer une gestion efficace du pipeline de Machine Learning.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
