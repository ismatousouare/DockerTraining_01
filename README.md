# Introduction à Docker
* Docker:Outil de virtualisation permettant de créer des images Docker
 Virtualise la couche application en utilisant le noyau de la machine hôte
* Systèmes supportés : Mac, Linux, Windows
## Différences entre Docker et les machines virtuelles (VM)
- VM : Virtualisent un système entier (noyau + application) et nécessitent un hyperviseur.
- Hyperviseur : Logiciel permettant à plusieurs systèmes d'exploitation de s'exécuter sur une seule machine physique
(exemples : VMware, VirtualBox)
- Docker : Virtualise uniquement la couche application en utilisant le noyau de la machine hôte
## Composants de Docker
* Docker Engine : Moteur principal permettant de créer, exécuter et gérer les conteneurs
* Images Docker : Exécutables créés à partir de Dockerfile
* Conteneurs : Instances d’images en cours d’exécution
## Creation et gestions des images docker
* Proces
  - Créer une image localement
  - Envoyer l'image sur un registre 
    - Exemples de registres:
      - Docker Hub (public)
      - Docker Registry(local)
      - Nexus(privé)
  - Récupération de l'image par d'autres utilisateurs
##  Outils:
* Docker compose: definit et gére des applications multi-conteneurs
* Terraform : un outil IaC (Infrastructure as Code)
## Systèmes d'exploitation (OS)
* Exemples:  Ubuntu, Debian, Fedora, CentOS, Kali Linux ...
## Conteneurs Docker
- Création:
  1. partir d'une image docker qui est un ensemble de fichier avec des instructions
  2. créer un ou plusieurs conteneurs à partir de cette image
- Fonctionnement: un conteneur est une image en cours d'exécution sur une machine physique, avec une adresse IP,
   pouvant utiliser des ports et manipuler des dossiers
## Installation 
### Par Script
```
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```
### Validation de l'installation
```
sudo docker version
```
### Ajouter l'utilisateur dans le groupe docker si c'est pas le cas
```
Sudo usermod -aG docker $USER 
```
NB: Apres l'ajout on redemarrer la machine
## Commande de base de docker
- Liste les images
```
docker images
```
## Recuperer une image
```
docker run --name container_name -it nom_image:tag_image {CMD -optionnelle}
```
## Lister les containers docker en exécution
```
docker ps
```
## Lister tous les containers docker(en exécution et en arrêt)
```
docker ps -a
```
- Supprimer un container
```
docker rm container_name__Or__container_id
```
- Supprimer un container en force
```
docker rm -f container_name__Or__container_id
```
- supprimer tous les conteniners sur ma machine en cours d'exécution ou à l'arrêt
```
docker rm -f $(docker ps -aq)
```
## Creer des images docker avec le fichier Dockerfile
Dans ce exemple nous allons le faire à partir de l'image debian 12.5
```
FROM debian:12.5
```
- Construction de l'image
```
docker build -t image_name:tag_image chemin ou se trouve le dockerfile
```
-Exemple:
```
 docker build -t firstimage:v01 .
```
-Demarrer l'image qui a été créer
```
docker run -it firstimage:v01 sh
```
-Installation de python3 dans l'image
```
RUN apt-get update && apt-get install -y python3
```
## Docker compose
### Installation 
Docker compose est installé en tant que plugin docker
```
services:
  site-1:
    image:  ubuntu/apache2:2.4-21.10_edge
    container_name: site1
    ports:
      -8081:80
```
* Demarrer les services 
```
docker compose up -d
```
# Apache2 sans docker
## Installation
```
sudo apt-get update
sudo apt-get install apache2
```
## Validation de l'installation
```
sudo service apache2 status
```
# Portenair: outil pour la gestions des conteneurs docker
## Exemple
-Ici on monte la dernière du portenair que l'on mappé sur le port 9000 avec toujours un redemarrage, et on a deux volumes qui sont montés
```
 portainer:
    image: portainer/portainer-ce:latest
    container_name: portainer
    restart: always
    ports:
      - "9000:9000"
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
      - portainer_data:/data
```
## creer un réseau externe => pas créer avec le docker compose
```
network create network_name
```
## supprimer un réseau 
```
docker network rm network_name
```
# Notes
- docker-compose qui la v1 est en python
- docker compose est la v2 de docker compos een golang
- docker compose est un outil qui permet de deployer des conteneurs avec des fichiers de configuration et developpéen open source
- chaque conteneur possède :
  - adresse ip
  - un nom de domaine au moins qui correspond au nom du conteneur
- Cache:  Système de stockage temporaire permettant de définir la durée de stockage des données
# Refernces
- https://docs.docker.com/engine/install/ubuntu/
- https://www.digitalocean.com/community/
- https://hub.docker.com/_/nginx
- https://docs.portainer.io/start/install-ce/server/docker/linux