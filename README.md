# Cours Docker

Docker est une plateforme open-source qui permet de créer, déployer et exécuter des applications dans des **conteneurs** –  
des environnements isolés et portables. Un conteneur regroupe tout le nécessaire pour faire fonctionner une application :  
le code, les bibliothèques et les dépendances, garantissant que l'application fonctionnera de manière identique sur n'importe quel environnement.  

L’avantage principal de Docker réside dans sa capacité à éviter les problèmes de compatibilité.  
Cela permet aux développeurs de travailler avec des environnements cohérents et uniformes,  
peu importe où l'application sera exécutée (localement, en production, etc.).  

## Différence entre conteneurs et machines virtuelles  

- **Conteneurs** : partagent le noyau du système d'exploitation de la machine hôte, sont légers, démarrent rapidement et consomment peu de ressources.  
- **Machines virtuelles (VM)** : sont isolées au niveau du noyau et nécessitent un OS complet, ce qui les rend plus lourdes et plus lentes à démarrer.  

## Docker vs Docker Compose vs Docker Swarm  

- **Docker** : gère les conteneurs individuellement.  
- **Docker Compose** : permet de gérer plusieurs conteneurs comme une application unifiée,  
utile pour définir et orchestrer les environnements multi-conteneurs pour le développement et les tests.  
- **Docker Swarm** : une solution de clustering pour déployer des applications conteneurisées à grande échelle.  

---

## Commandes Docker

### Commandes de base

| Commande                      | Description |
|-------------------------------|-------------|
| `docker --version`            | Vérifie la version de Docker installée. |
| `docker pull <image>`         | Télécharge une image depuis Docker Hub. |
| `docker run <image>`          | Crée et exécute un conteneur basé sur une image. |
| `docker ps`                   | Affiche les conteneurs actifs. |
| `docker ps -a`                | Affiche tous les conteneurs (actifs et inactifs). |
| `docker stop <container_id>`  | Arrête un conteneur actif. |
| `docker start <container_id>` | Démarre un conteneur stoppé. |
| `docker rm <container_id>`    | Supprime un conteneur inactif. |
| `docker rmi <image>`          | Supprime une image. |

### Commandes pour créer des images

| Commande                         | Description |
|----------------------------------|-------------|
| `docker build -t <name> .`       | Construit une image à partir d'un Dockerfile dans le répertoire actuel. |
| `docker images`                  | Liste toutes les images locales. |
| `docker tag <image> <new_tag>`   | Ajoute un tag à une image existante. |
| `docker push <name:tag>`         | Envoie une image sur Docker Hub (après s'être authentifié). |

### Commandes pour les conteneurs

| Commande                             | Description |
|--------------------------------------|-------------|
| `docker exec -it <container_id> bash`| Accède au terminal d'un conteneur en cours d'exécution. |
| `docker logs <container_id>`         | Affiche les logs d'un conteneur. |
| `docker inspect <container_id>`      | Affiche des informations détaillées sur un conteneur. |
| `docker cp <container_id>:/path /host_path` | Copie un fichier d’un conteneur vers l’hôte. |
| `docker commit <container_id> <new_image>` | Crée une nouvelle image depuis un conteneur modifié. |

### Docker Compose

Docker Compose est un outil pour définir et exécuter des applications multi-conteneurs. Il utilise un fichier `docker-compose.yml` pour configurer les services.

Exemple de `docker-compose.yml` pour une application avec une base de données MySQL :

```yaml
version: '3'
services:
  web:
    image: nginx:latest
    ports:
      - "80:80"
  database:
    image: mysql:latest
    environment:
      MYSQL_ROOT_PASSWORD: example
```

### Commandes Docker Compose

| Commande               | Description                                                |
|------------------------|------------------------------------------------------------|
| `docker-compose up`    | Démarre les services définis dans `docker-compose.yml`.    |
| `docker-compose up -d` | Démarre les services en mode détaché (en arrière-plan).    |
| `docker-compose down`  | Arrête et supprime les conteneurs, réseaux et volumes créés. |
| `docker-compose ps`    | Liste les conteneurs gérés par Docker Compose.             |
| `docker-compose logs`  | Affiche les logs de tous les services.                     |
| `docker-compose build` | Construit les images spécifiées dans le fichier.           |

### Commandes avancées

| Commande                    | Description                                                         |
|-----------------------------|---------------------------------------------------------------------|
| `docker network ls`         | Liste les réseaux Docker.                                           |
| `docker network create <name>` | Crée un réseau personnalisé.                                 |
| `docker volume ls`          | Liste les volumes Docker.                                          |
| `docker volume create <name>` | Crée un volume pour stocker des données persistantes.          |
| `docker system prune`       | Supprime les conteneurs, images et volumes inutilisés pour libérer de l’espace. |

Exemple de Workflow avec Docker

	1.	Télécharger une image : docker pull nginx
	2.	Créer et exécuter un conteneur : docker run -d -p 8080:80 nginx
	3.	Accéder au conteneur : docker exec -it <container_id> bash
	4.	Voir les logs : docker logs <container_id>
	5.	Arrêter le conteneur : docker stop <container_id>
	6.	Supprimer le conteneur : docker rm <container_id>

Docker est un outil puissant qui facilite le développement, la gestion et le déploiement d’applications grâce à la conteneurisation.  
