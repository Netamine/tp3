## Projet de Prédiction de l'Espèce d'Iris avec Streamlit, FastAPI, MLflow et Docker-Compose

### Contexte
La classification de l'espèce d'une fleur d'Iris est un problème de prédiction classique en machine learning, souvent utilisé pour démontrer les concepts de classification et de modélisation. Ce projet vise à automatiser et à améliorer ce processus de décision à l'aide de techniques modernes de machine learning et de déploiement d'applications.

### Objectif
Construire un pipeline de machine learning (ML) pour prédire l'espèce d'Iris en fonction de ses caractéristiques, afin de rendre les processus d'identification plus efficaces et ciblés.

### Aperçu Technique
Ce projet intègre les outils et technologies suivants :
- **Streamlit** pour le frontend : Créer une interface utilisateur interactive.
- **FastAPI** pour le backend : Déployer une API RESTful pour la prédiction de l'espèce d'Iris.
- **MLflow** pour la gestion des modèles : Suivre et gérer les expériences de modélisation.
- **Docker et Docker-Compose** pour la containerisation : Faciliter le déploiement et la gestion des services.

### Composants du Pipeline

1. **Acquisition et Prétraitement des Données** : Chargement et préparation des données du dataset Iris.
2. **Entraînement de modèles ML avec suivi MLflow** : Utilisation de MLflow pour suivre les expériences et les modèles entraînés.
3. **Déploiement du meilleur modèle via FastAPI** : Création d'une API RESTful pour servir le modèle prédictif.
4. **Interface utilisateur Streamlit** : Interface web pour interagir avec le modèle via le point de terminaison FastAPI.
5. **Containerisation avec Docker et Docker-Compose** : Déploiement de l'ensemble du projet dans des conteneurs Docker orchestrés par Docker-Compose.

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
