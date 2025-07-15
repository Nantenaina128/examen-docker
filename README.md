README - Concepts Docker
1. Docker Image
Une image Docker est un modèle en lecture seule qui contient les instructions pour créer un conteneur Docker. Elle inclut le système d'exploitation, les logiciels, les bibliothèques et le code applicatif.

Commandes principales:

bash
# Lister les images locales
docker images

# Télécharger une image depuis Docker Hub
docker pull nom_image:tag

# Construire une image depuis un Dockerfile
docker build -t nom_image .

# Supprimer une image
docker rmi nom_image
2. Docker Container
Un conteneur est une instance exécutable d'une image Docker. C'est un environnement isolé qui exécute les applications.

Commandes principales:

bash
# Lancer un nouveau conteneur
docker run -d --name mon_conteneur nom_image

# Lister les conteneurs (en cours d'exécution)
docker ps

# Lister tous les conteneurs (y compris arrêtés)
docker ps -a

# Arrêter un conteneur
docker stop mon_conteneur

# Démarrer un conteneur arrêté
docker start mon_conteneur

# Supprimer un conteneur
docker rm mon_conteneur
3. Dockerfile
Un Dockerfile est un script texte qui contient toutes les commandes nécessaires pour construire une image Docker.

Exemple de Dockerfile:

dockerfile
FROM ubuntu:20.04
RUN apt-get update && apt-get install -y python3
COPY . /app
WORKDIR /app
CMD ["python3", "app.py"]
Commandes principales:

bash
# Construire une image depuis un Dockerfile
docker build -t mon_image .

# Spécifier un fichier Dockerfile différent
docker build -f Dockerfile.dev -t mon_image .
4. Docker Compose
Docker Compose est un outil pour définir et exécuter des applications Docker multi-conteneurs à l'aide d'un fichier YAML.

Exemple de docker-compose.yml:

yaml
version: '3'
services:
  web:
    build: .
    ports:
      - "5000:5000"
  redis:
    image: "redis:alpine"
Commandes principales:

bash
# Démarrer les services
docker-compose up -d

# Arrêter les services
docker-compose down

# Lister les services en cours
docker-compose ps

# Reconstruire et redémarrer les services
docker-compose up --build
5. Docker Volume
Les volumes Docker sont le mécanisme préféré pour persister les données générées et utilisées par les conteneurs Docker.

Commandes principales:

bash
# Créer un volume
docker volume create mon_volume

# Lister les volumes
docker volume ls

# Inspecter un volume
docker volume inspect mon_volume

# Supprimer un volume
docker volume rm mon_volume

# Monter un volume dans un conteneur
docker run -v mon_volume:/chemin/dans/conteneur nom_image
Bonnes pratiques
Utilisez des images officielles quand c'est possible

Gardez vos images aussi petites que possible

Utilisez des volumes pour les données persistantes

Une seule préoccupation par conteneur

Documentez vos Dockerfiles avec des commentaires


