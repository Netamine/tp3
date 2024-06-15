### README.md

# Projet de Prédiction des Espèces d'Iris avec Streamlit, FastAPI, MLflow et Docker Compose

## Description

Ce projet est une application de machine learning pour prédire les espèces d'Iris en utilisant les caractéristiques de la fleur. L'application utilise Streamlit pour l'interface utilisateur, FastAPI pour le backend, MLflow pour la gestion des modèles, et Docker Compose pour le déploiement. Le modèle est entraîné sur le jeu de données Iris et enregistré avec MLflow.

## Installation et Utilisation

### Prérequis

- Docker
- Docker Compose

### Étapes d'installation

1. Copier le contenu

2. Construisez et démarrez les services Docker :
   ```bash
   docker-compose up --build
   ```

### Utilisation

Une fois les services démarrés, les composants suivants seront disponibles :

- **Streamlit (Frontend)** : [http://localhost:8001](http://localhost:8001)
- **FastAPI (Backend)** : [http://localhost:8002](http://localhost:8002)
- **MLflow** : [http://localhost:8003](http://localhost:8003)

### Instructions pour exécuter les services

#### Streamlit (Frontend)

Streamlit est utilisé pour l'interface utilisateur permettant de saisir les caractéristiques de la fleur d'Iris et de recevoir des prédictions.

- URL : [http://localhost:8001](http://localhost:8001)

#### FastAPI (Backend)

FastAPI gère les requêtes de prédiction en utilisant le modèle chargé.

- URL : [http://localhost:8002](http://localhost:8002)
- Endpoint de prédiction : `/predict`
  - Méthode : POST
  - Paramètres JSON :
    ```json
    {
      "sepal_length": float,
      "sepal_width": float,
      "petal_length": float,
      "petal_width": float
    }
    ```

#### MLflow

MLflow est utilisé pour la gestion des expériences et des modèles.

- URL : [http://localhost:8003](http://localhost:8003)

### Détails supplémentaires

- Les modèles sont sauvegardés dans le répertoire `./models`.
- Les expériences MLflow sont sauvegardées dans le répertoire `~/session4/tp3/mlflow/mlruns`.

---

### Documentation des fichiers

#### `docker-compose.yaml`

Définit les services Docker pour le frontend, backend, et MLflow.

#### `frontend/Dockerfile`

Configure le conteneur Docker pour Streamlit.

#### `frontend/main.py`

Code Streamlit pour l'interface utilisateur.

#### `backend/Dockerfile`

Configure le conteneur Docker pour FastAPI.

#### `backend/main.py`

Code FastAPI pour gérer les prédictions.

#### `mlflow/Dockerfile`

Configure le conteneur Docker pour MLflow.

#### `mlflow/metrics.py`

Script pour entraîner le modèle, évaluer les performances et enregistrer le modèle avec MLflow.

---

### Commandes pour Docker Compose

- **Construire et démarrer les services :**
  ```bash
  docker-compose up --build
  ```

- **Arrêter les services :**
  ```bash
  docker-compose down
  ```

- **Recréer les services (si nécessaire) :**
  ```bash
  docker-compose up --force-recreate
  ```

---

### Références

- [Streamlit](https://streamlit.io/)
- [FastAPI](https://fastapi.tiangolo.com/)
- [MLflow](https://mlflow.org/)
- [Docker Compose](https://docs.docker.com/compose/)

