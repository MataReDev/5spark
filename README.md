# 5SPAR Project - Analyse des Sentiments en Temps Réel
## Description
Ce projet vise à analyser les données de Mastodon en temps réel et à effectuer une analyse de sentiments à l'aide de Spark, Kafka, et PostgreSQL. Les résultats sont visualisés avec des bibliothèques Python comme Matplotlib et Seaborn.

## Prérequis
1. Mastodon
2. Docker
3. Docker Compose
4. Python 3.x
5. Java (pour PySpark)

## Installation
### Créer application sur Mastodon

Aller sur ce site : [Nouvelle Mastodon Application](https://mastodon.social/settings/applications/new)
Mettez vos préférence pour les droits de l'API (De préférence admin:read)

Récupérer le token et remplacer le dans le Part1.


### Lancer les conteneurs Docker
Le fichier docker-compose.yml est utilisé pour configurer et lancer les services nécessaires, notamment Kafka, Zookeeper, PostgreSQL et Spark.

Pour lancer les services Docker, exécutez la commande suivante dans le répertoire racine du projet :

```bash
docker-compose up -d
```
### Récupérer le token Jupyter Notebook
Une fois les services Docker lancés, vous pouvez récupérer le token Jupyter en exécutant la commande suivante : 

```bash
docker exec -it jupyterContainer jupyter notebook list
```

### Créer le topic dans kafka
```bash
kafka-topics.sh --create --topic mastodonstream --bootstrap-server 192.168.1.10:9092 --partitions 3 --replication-factor 1
```

### Installation des dépendances Python
Avant de pouvoir exécuter les notebooks Jupyter, vous devez installer toutes les dépendances Python nécessaires. Utilisez le fichier Part0.ipynb fourni pour installer ces dépendances :
Cela installera toutes les bibliothèques requises, y compris PySpark, Kafka, Mastodon.py, et les bibliothèques pour l'analyse de données.

### Exécution des notebooks
Accédez à Jupyter Notebook en utilisant le token récupéré précédemment, et naviguez jusqu'au dossier `notebooks`. Vous y trouverez les notebooks nécessaires pour l'analyse de données et la visualisation des résultats.

## Structure du projet
- `docker-compose.yml` : Fichier Docker Compose pour configurer les services nécessaires (Kafka, Zookeeper, PostgreSQL, Spark).
- `notebooks/` : Dossier contenant les notebooks Jupyter pour l'analyse de données.
- `requirements.txt` : Liste des dépendances Python à installer.
