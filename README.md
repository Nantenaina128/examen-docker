# examen-docker
  📦 1. Commandes de base
Commande	Description
docker --version	Affiche la version de Docker
docker info	Donne les infos du système Docker
docker ps	Liste des conteneurs actifs
docker ps -a	Liste tous les conteneurs (même arrêtés)
docker images	Liste les images Docker locales
docker rm [id]	Supprimer un conteneur
docker rmi [image]	Supprimer une image

🚀 2. Lancer un conteneur
bash
Copier
Modifier
docker run hello-world
bash
Copier
Modifier
docker run -it ubuntu bash
Option	Description
-it	Mode interactif (terminal)
--rm	Supprime le conteneur à la fin
-d	Mode détaché (en arrière-plan)
-p 8080:80	Redirige le port 80 du conteneur vers 8080 sur l’hôte

📁 3. Volumes (partage de fichiers)
bash
Copier
Modifier
docker run -v /chemin/local:/chemin/conteneur image
Exemple
docker run -v $(pwd):/app ubuntu

🛠️ 4. Images et Docker Hub
Commande	Description
docker pull nginx	Télécharger une image
docker build -t monimage .	Créer une image à partir d’un Dockerfile
docker push monuser/monimage	Pousser une image vers Docker Hub

🔁 5. Gestion des conteneurs
Commande	Description
docker start [id]	Démarrer un conteneur
docker stop [id]	Stopper un conteneur
docker exec -it [id] bash	Ouvrir un terminal dans un conteneur
docker logs [id]	Voir les logs d’un conteneur

📄 6. Dockerfile – Structure de base
Un Dockerfile est un fichier texte qui contient les instructions pour construire une image Docker.

Exemple simple : Dockerfile pour une app Python
Dockerfile
Copier
Modifier
# Image de base
FROM python:3.10

# Répertoire de travail
WORKDIR /app

# Copier les fichiers dans l'image
COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .

# Commande pour démarrer l'app
CMD ["python", "app.py"]
Principales instructions Dockerfile
Instruction	Description
FROM	Définit l’image de base
WORKDIR	Définit le répertoire de travail
COPY	Copie les fichiers vers l’image
RUN	Exécute une commande pendant la construction
CMD	Commande par défaut à l’exécution
EXPOSE	Indique les ports utilisés
ENV	Définit une variable d’environnement

🧪 7. Construire et exécuter une image personnalisée
bash
Copier
Modifier
docker build -t monapp .
docker run -it monapp
⚠️ 8. Nettoyage
Commande	Description
docker system prune	Supprimer tout ce qui est inutilisé (dangereux !)
docker image prune	Supprimer les images inutilisées
docker volume prune	Supprimer les volumes non utilisés

📚 Bonus : Docker Compose (multi-conteneurs)
Fichier docker-compose.yml :

yaml
Copier
Modifier
version: '3'
services:
  web:
    image: nginx
    ports:
      - "8080:80"
Lancer :

bash
Copier
Modifier
docker-compose up -d# examen-docker
