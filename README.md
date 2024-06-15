## Projet de Prédiction de l'Espèce d'Iris avec Streamlit, FastAPI, MLflow et Docker-Compose

### Contexte
La classification de l'espèce d'une fleur d'Iris est un problème de prédiction classique en machine learning, souvent utilisé pour démontrer les concepts de classification et de modélisation. Ce projet vise à automatiser et à améliorer ce processus de décision à l'aide de techniques modernes de machine learning et de déploiement d'applications.

### Objectif
Le but de ce projet est de développer un système efficace pour prédire l'espèce d'Iris, facilitant ainsi la prise de décision basée sur les caractéristiques mesurées des fleurs en utilisant les outils Streamlit, FastAPI et MLflow

### Aperçu Technique
Ce projet intègre les outils et technologies suivants :
- **Streamlit** pour le frontend : Créer une interface utilisateur interactive.
- **FastAPI** pour le backend : Déployer une API RESTful pour la prédiction de l'espèce d'Iris.
- **MLflow** pour la gestion des modèles : Suivre et gérer les expériences de modélisation.
- **Docker et Docker-Compose** pour la containerisation : Faciliter le déploiement et la gestion des services.

## Éléments du Pipeline de Machine Learning

1. **Collecte et Prétraitement des Données** :
   - Chargement et préparation des données du dataset Iris.

2. **Entraînement des Modèles Machine Learning avec Suivi MLflow** :
   - Utilisation de MLflow pour organiser et suivre les différentes expériences de modélisation. Cela inclut l'entraînement de divers modèles et la comparaison de leurs performances pour sélectionner le modèle optimal.

3. **Service du Modèle via FastAPI** :
   - Mise en place d'une API RESTful avec FastAPI pour exposer le modèle prédictif. Cette API permet aux applications externes de soumettre des données et de recevoir des prédictions en retour.

4. **Interface Utilisateur avec Streamlit** :
   - Création d'une interface utilisateur interactive en utilisant Streamlit, permettant aux utilisateurs finaux de soumettre des données et de voir les prédictions générées par le modèle via l'API FastAPI.

5. **Containerisation avec Docker et Docker-Compose** :
   - Utilisation de Docker pour containeriser les applications backend, frontend, et MLflow. Docker-Compose est utilisé pour orchestrer ces conteneurs, simplifiant ainsi le déploiement et la gestion du projet dans divers environnements.

6. **Déploiement et Gestion des Modèles avec MLflow** :
   - Une fois les conteneurs lancés, pour gérer les modèles, vous pouvez exécuter le conteneur MLflow et accéder à un shell bash pour enregistrer et gérer les modèles. Voici les étapes :
     - Après avoir lancé les services avec Docker-Compose, exécutez la commande suivante pour accéder au conteneur MLflow :
       ```bash
       docker exec -it mlflow bash
       ```
     - À partir du shell du conteneur, vous pouvez exécuter des scripts ou des commandes pour entraîner votre modèle, évaluer ses performances, et enregistrer le modèle dans le répertoire `models` avec un suffixe de date pour indiquer le moment de l'entraînement :
       ```bash
       # Exemple de commande pour entraîner un modèle et sauvegarder le fichier
       python3 /app/metrics.py
       ```
     - Ce script entraînera un modèle, évaluera ses performances, et enregistrera le modèle dans le dossier `models` avec un nom incluant un timestamp, facilitant le suivi des différentes versions du modèle.
    
### Structure du Dossier de Projet

```
TP3/
│
├── backend/
│   ├── Dockerfile
│   ├── main.py
│
├── docker-compose.yaml
│
├── frontend/
│   ├── Dockerfile
│   ├── main.py
│
├── mlflow/
│   ├── Dockerfile
│   ├── metrics.py
│   └── mlruns/         # Artéfacts des expériences d'entraînement ML
│
├── models/             # Modèles enregistrés
    ├── model_2024_06_15_T03_14_31.pkl
    ├── model_2024_06_15_T03_23_08.pkl
    └── model.pkl
```

### Instructions pour l'Exécution

1. **Construire et démarrer les services avec Docker-Compose** :
   - Ouvrez un terminal et placez-vous dans le dossier du projet.
   - Exécutez la commande suivante pour construire et lancer les services :
     ```bash
     docker-compose up --build
     ```
   - Cette commande construira les images Docker pour chaque service (backend, frontend, mlflow) et les démarrera selon la configuration définie dans `docker-compose.yaml`.

2. **Accéder aux services** :
   - **FastAPI** : Accédez à l'API RESTful pour la prédiction de l'espèce d'Iris via `http://localhost:8002`.
   - **Streamlit** : Interagissez avec l'interface utilisateur de Streamlit pour soumettre des données pour prédiction à `http://localhost:8001`.
   - **MLflow** : Visualisez les expériences et les métriques de vos modèles sur l'interface MLflow à `http://localhost:8003`.

### Détails des Composants

- **Backend** :
  - `Dockerfile` : Contient les instructions pour construire l'image Docker du service backend utilisant FastAPI.
  - `main.py` : Script Python pour déployer et servir le modèle en tant que point de terminaison FastAPI.

- **Frontend** :
  - `Dockerfile` : Dockerfile pour construire l'image Docker du service frontend utilisant Streamlit.
  - `main.py` : Code Python pour l'application web Streamlit, qui permet aux utilisateurs de soumettre des données pour prédiction via FastAPI.

- **MLflow** :
  - `Dockerfile` : Dockerfile pour exécuter l'interface utilisateur de MLflow.
  - `metrics.py` : Script pour évaluer le modèle et enregistrer les résultats avec MLflow.
  - `mlruns/` : Dossier pour stocker les artéfacts des expériences d'entraînement MLflow.

- **Models** :
  - Contient les modèles enregistrés après leur entraînement.

- **docker-compose.yaml** : Fichier de configuration pour orchestrer les services backend, frontend, et MLflow.

Ce projet offre une solution complète pour la prédiction de l'espèce d'Iris, intégrant les meilleures pratiques en matière de machine learning, de développement web, et de containerisation. Il illustre comment les technologies modernes peuvent être combinées pour créer des systèmes ML robustes et facilement déployables.
